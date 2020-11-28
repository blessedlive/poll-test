<template>
    <div class="poll-constructor--item" :class="condition ? condition.color : ''">
        <div class="row">
            <b>Условие {{ index + 1 }}</b>
            <select class="select-input" v-model="condition.name">
                <option>Выберите условие</option>
                <option v-for="(item, i) in conditionList" :value="item.name" :key="i">{{ item.name }}</option>
            </select>
        </div>
        <div class="poll-constructor--controls" v-if="condition.item"> 
            <div class="row" v-for="(conditionValue, i) in condition.values" :key="i">
                <span class="type"><div class="type--extra" v-if="i > 0">или</div> {{ condition.item }} {{ i + 1 }}</span>
                <div class="range-group" v-if="condition.type === 'range'">
                    <div class="range-input">
                        <span>от</span>
                        <input type="number" v-model="condition.values[i].min">
                    </div>
                    <div class="range-input">
                        <span>до</span>
                        <input type="number" v-model="condition.values[i].max">
                    </div>
                </div>            
                <select class="select-input" v-if="condition.type === 'select'" v-model="condition.values[i]">
                    <option>Выберите {{ condition.item.toLowerCase() }}</option>
                    <option v-for="value in condition.defaultValues" :key="value">{{ value }}</option>
                </select>
            </div>
            <div class="poll-constructor--buttons">
                <button class="green" @click="addConditionValue">+ Добавить {{ condition.item.toLowerCase() }} </button>
                <button class="red" @click="removeCondition">Удалить условие</button>
            </div>
        </div>
    </div> 
</template>

<script>
export default {
    watch: {
        'condition.name'(val, oldVal) {
            this.$parent.changeType(this.index, val);
        }
    },

    methods: {
        addConditionValue() {
            this.$parent.addConditionValue(this.index);
        },

        removeCondition() {
            this.$parent.removeCondition(this.index);
        }
    },

    props: {
        index: Number,
        condition: Object,
        conditionList: Array
    }
}
</script>

<style scoped>
.poll-constructor--item {
    display: flex;
    position: relative;
    width: 100%;
    padding: 40px;
    flex-direction: column;
    border-bottom: 1px solid rgba(25, 73, 27, 0.3);
}

.poll-constructor--item .row {
    margin: 20px 0;
}

.poll-constructor--item b {
    font-size: 20px;
    font-weight: 700;
}

.poll-constructor--item .type {
    display: flex;
    font-size: 16px;
    align-items: center;
}

.poll-constructor--item .type .type--extra {
    display: flex;
    padding: 10px 15px;
    background: rgba(0,0,0,.1);
    border-radius: 5px;
    margin-right: 10px;
    align-items: center;
}

.row b, .type {
    width: 30%;
}

.row .select-input, .range-group {
    width: 70%;
}

.poll-constructor--item .range-group {
    display: flex;
}

.range-group input {
    padding: 10px 20px;
    border: 2px solid rgb(187, 187, 187);
    border-radius: 5px;
    font-size: 20px;
    max-width: 100px;
    margin: 0 10px;
}

.poll-constructor--item .select-input {
    padding: 10px 20px;
    border: 2px solid rgb(187, 187, 187);
    border-radius: 5px;
    font-size: 20px;
}

.poll-constructor--item::before {
    content: "И";
    display: flex;
    justify-content: center;
    align-items: center;
    width: 60px;
    height: 40px;
    background: rgba(0,0,0,.1);
    color: #000;
    top: -20px;
    left: 40px;
    position: absolute;
    border-radius: 5px;
    border: 1px solid rgba(25, 73, 27, 0.3);
}

.poll-constructor--item:first-child::before {
    content: none;
}

.poll-constructor--item.light, .poll-constructor--item.light::before {
    background: #fffcf5;
}

.poll-constructor--item.blue, .poll-constructor--item.blue::before {
    background: #f8faff;
}

.poll-constructor--item.green, .poll-constructor--item.green::before {
    background: #fafff8;
}

.poll-constructor--buttons {
    display: flex;
    margin-top: 35px;
    padding-left: 30%;
    justify-content: space-between;
}

.poll-constructor--buttons button {
    padding: 10px 20px;
    font-size: 18px;
    border-radius: 5px;
    background: #fff;
    outline: none;
    border: none;
    cursor: pointer;
}

.poll-constructor--buttons button.green {
    color: rgb(77, 158, 77);
    border: 2px solid rgb(118, 221, 118);
    box-shadow: 0 0 10px rgba(0, 128, 0, 0.125);
}

.poll-constructor--buttons button.red {
    color: rgb(158, 77, 77);
    border: 2px solid rgb(221, 118, 118);
    box-shadow: 0 0 10px rgba(128, 0, 0, 0.125);
}
</style>