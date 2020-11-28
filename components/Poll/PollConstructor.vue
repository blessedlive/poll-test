<template>
    <div class="polls-constructor">
        <h4>Добавить опрос</h4>
        <div class="poll-constructor--items">
            <PollItem 
                v-for="(condition, index) in conditions" 
                :condition="condition"
                :index="index"
                :conditionList="conditionList"
                :key="index"
            />
        </div>
        <div class="poll-constructor--add" @click="addCondition">
            <span class="plus">+</span>
            <span>Нажмите, чтобы добавить новое условие выборки.<br>Все условия связываются между собой логическим "И"</span>
        </div>
        <div class="poll-constructor--footer">
            <button class="test-btn">Протестировать опрос</button>
            <button class="next-btn" @click="sendServer">Далее</button>
        </div>
    </div>
</template>

<style scoped>
.polls-constructor {
    display: flex;
    width: 100%;
    flex-direction: column;
    padding-top: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.15);
}

.polls-constructor h4 {
    font-size: 18px;
    font-weight: 700;
    color: rgb(141, 141, 141);
    padding: 10px 30px;
    margin-bottom: 20px;
}

.poll-constructor--items {
    display: flex;
    width: 100%;
    flex-direction: column;
}

.poll-constructor--add {
    display: flex;
    margin: 10px;
    padding: 20px;
    border: 2px solid rgb(141, 141, 141);
    justify-content: center;
    align-items: center;
    color: green;
    flex-direction: column;
    text-align: center;
    cursor: pointer;
    font-size: 20px;
    border-radius: 5px;
    transition: all 0.15s ease-in-out;
}

.poll-constructor--add .plus {
    font-size: 42px;
    margin-bottom: 5px;
}

.poll-constructor--add:hover {
    border: 2px solid green;
}

.poll-constructor--footer {
    display: flex;
    padding: 20px;
    background: #fafafa;
    justify-content: space-between;
}

.poll-constructor--footer button {
    padding: 20px;
    font-size: 20px;
    border-radius: 5px;
    background: #fff;
    outline: none;
    border: none;
    cursor: pointer;
}

.poll-constructor--footer button.test-btn {
    color: rgb(77, 158, 77);
    border-bottom: 1px solid rgba(0, 0, 0, 0.15);
    box-shadow: 0 0 10px rgba(0, 128, 0, 0.125);
}

.poll-constructor--footer button.next-btn {
    color: #fff;
    border: 2px solid rgb(74, 155, 74);
    box-shadow: 0 0 10px rgba(0, 128, 0, 0.125);
    background: rgb(74, 155, 74); 
}
</style>

<script>
import PollItem from './PollItem';

export default {
    data: () => {
        return {
            conditionList: [{
                name: "Возраст респондента",
                type: "range",
                color: "light",
                item: "Диапазон",
            },{
                name: "Тип карты лояльности",
                type: "select",
                defaultValues: ['Gold', 'Silver', 'Bronze'],
                item: "Тип",
                color: "blue"
            },{
                name: "Статус карты лояльности",
                type: "select",
                defaultValues: ['Активна', 'Неактивна'],
                item: "Статус",
                color: "green"
            }],

            conditions: []
        }
    },

    methods: {
        removeCondition(index) {
            this.conditions.splice(index, 1);
        },

        addCondition() {
            this.conditions.push({ name: "Выберите условие" })
        },

        changeType(index, conditionName) {
            const condition = this.conditionList.find(a => a.name === conditionName);
            this.$set(this.conditions, index, Object.assign({}, condition));
        },

        addConditionValue(index) {
            if(!this.conditions[index].values) {
                this.$set(this.conditions[index], 'values', []);  
            }

            const conditionValue = (this.conditions[index].type === "range") ? { min: 0, max: 0 } : null
            this.conditions[index].values.push(conditionValue);
        },

        sendServer() {
            if(!this.conditions.length) {
                return alert("Вы не добавили условия")
            }

            for(const condition of this.conditions) {
                if(!condition.values) {
                    return alert("Вы не выбрали варианты для условия")
                }

                for(const value of condition.values) {
                    if(condition.type === "select" && !condition.defaultValues.includes(value)) {
                        return alert("Вы не выбрали варианты для условия")
                    }
                }
            }

            this.$axios.post("/api/polls/send", {
                conditions: this.conditions
            }).then(r => {
                alert("Отправлено!")
            });
        }
    },
    
    components: {
        PollItem
    }
}
</script>