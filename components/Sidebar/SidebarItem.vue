<template>
    <nuxt-link class="sidebar-item" :to="link">
        <slot></slot>
        <span class="sidebar-item__name">{{ name }}</span>
    </nuxt-link>
</template>

<style>

.sidebar-item {
    display: flex;
    flex-direction: column;
    width: 100%;
    min-height: 150px;
    justify-content: center;
    align-items: center;
    text-decoration: none;
    border-radius: 15px;
    border: 2px solid transparent;
    transition: all 0.15s ease-in-out;
    margin: 10px 0;
}

.sidebar-item svg {
    align-self: center; 
    width: 60px;
    margin-bottom: 10px;
    transition: all 0.15s ease-in-out;
}

.sidebar-item .sidebar-item__name {
    color: #000;
    font-size: 16px;
    transition: all 0.15s ease-in-out;
}

.sidebar-item:hover {
    border: 2px solid #93bc02;
}

.sidebar-item:hover .sidebar-item__name {
    color: #93bc02;
}

.sidebar-item:hover svg {
    fill: #93bc02;
}

.sidebar-item.nuxt-link-active {
    background: #f7f7f7;
}

.sidebar-item.nuxt-link-active .sidebar-item__name {
    font-weight: 700;
}

</style>

<script>
export default {
    props: {
        name: String,
        link: String
    }
}
</script>