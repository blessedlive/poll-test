<template>
    <div class="search-bar">
        <input class="search-bar__input" placeholder="Поиск по системе">
        <SearchIcon/>
    </div>
</template>

<script>
import SearchIcon from '@/assets/images/search.svg';

export default {
    components: { SearchIcon }
}
</script>

<style scoped>
.search-bar {
    display: flex;
    width: 100%;
    height: 50px;
    position: relative;
}

.search-bar .search-bar__input {
    width: 100%;
    border-radius: 5px;
    padding: 10px 60px 10px 20px;
    color: grey;
    font-size: 18px;
    outline: none;
    border: 2px solid #000;
}

.search-bar svg {
    position: absolute;
    top: 10px;
    right: 20px;
    width: 30px;
}
</style>