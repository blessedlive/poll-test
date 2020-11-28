<template>
    <div class="polls-navbar">
        <nuxt-link to="/polls/settings">
            <span>Параметры</span>
        </nuxt-link>
        <nuxt-link to="/polls/questions">
            <span>Вопросы</span>
        </nuxt-link>
        <nuxt-link to="/polls/logic">
            <span>Логика</span>
        </nuxt-link>
        <nuxt-link to="/polls/conditions">
            <span>Условия</span>
        </nuxt-link>
        <nuxt-link to="/polls/respondents">
            <span>Респонденты</span>
        </nuxt-link>
    </div>
</template>

<script>
export default {
    
}
</script>

<style scoped>
.polls-navbar {
    display: flex;
    width: 100%;
    border-bottom: 1px solid #9dbd2d;
}

.polls-navbar a {
    display: flex;
    width: 18%;
    height: 60px;
    font-size: 22px;
    color: #1b7e2f;
    text-decoration: none;
    justify-content: center;
    align-items: center;
    transition: all 0.15s ease-in-out;
    border-bottom: 1px solid transparent;
}

.polls-navbar a:hover {
    border-bottom: 2px solid #9dbd2d;
}

.polls-navbar a.nuxt-link-exact-active {
    font-weight: 700;
    color: #000;
    border-bottom: 2px solid #9dbd2d;
}
</style>