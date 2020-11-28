<template>
    <div class="user-info">
        <img :src="avatar" :alt="name"/>
        <div class="user-info--text">
            <span class="user-info--name">{{ name }}</span>
            <span class="user-info--role">{{ role }}</span>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        name: String,
        avatar: String,
        role: String
    }
}
</script>

<style scoped>
.user-info {
    display: flex;
    width: 100%;
    justify-content: center;
    align-items: center;
}

.user-info img {
    border-radius: 50%;
    width: 80px;
}

.user-info--text {
    display: flex;
    flex-direction: column;
    margin-left: 10px;
}

.user-info--name {
    font-weight: 700;
    font-size: 20px;
}

.user-info--role {
    color: grey;
    font-size: 16px;
}
</style>