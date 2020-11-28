<template>
    <div class="layout">
        <div class="sidebar-wrapper">
            <Sidebar />
        </div>
        <div class="container">
            <Header/>
            <div class="content">
                <Nuxt />
            </div>
        </div>
    </div>
</template>

<script>
import Header from '@/components/Header';
import Sidebar from '@/components/Sidebar/Sidebar';

export default {
    components: { Header, Sidebar }
}
</script>
