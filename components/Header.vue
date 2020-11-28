<template>
    <header>
        <div class="row between align-center">
            <div class="search-bar-wrapper">
                <SearchBar/>
            </div>
            <div class="user-info-wrapper">
                <UserInfo avatar="https://i.pinimg.com/236x/7c/ab/18/7cab184c5e791921ed607e23458492b6.jpg" role="Администратор" name="Alexander C."/>
            </div>
        </div>
    </header>
</template>

<style scoped>
header {
    padding: 20px 40px;
}

header .search-bar-wrapper {
    width: 50%;
}
</style>

<script>
import SearchBar from '@/components/SearchBar';
import UserInfo from '@/components/UserInfo';

export default {
    components: { SearchBar, UserInfo }
}
</script>