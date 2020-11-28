<template>
    <div class="sidebar">
        <Logo/>

        <div class="sidebar__menu">
            <SidebarItem name="Опросы" link="/polls/settings">
                <component :is="'PollIcon'"/>
            </SidebarItem>
            <SidebarItem name="Пользователи" link="/users">
                <component :is="'GroupIcon'"/>
            </SidebarItem>
            <SidebarItem name="Черные списки" link="/blacklist">
                <component :is="'FlagIcon'"/>
            </SidebarItem>
            <SidebarItem name="Колл-центр" link="/call">
                <component :is="'CallIcon'"/>
            </SidebarItem>
        </div>
    </div>
</template>

<style scoped>
    .sidebar {
        display: flex;
        width: 100%;
        flex-direction: column;
        min-height: 100vh;
        border-right: 1px solid rgb(200, 200, 200);
        padding: 40px 0;
        align-items: center;
    }

    .sidebar__menu {
        display: flex;
        width: 100%;
        margin-top: 70px;
        flex-direction: column;
        padding: 0 20px;
    }
</style>

<script>
import Logo from '@/components/Logo';
import SidebarItem from './SidebarItem';

/* Icons */
import PollIcon from '@/assets/images/files.svg';
import GroupIcon from '@/assets/images/group.svg';
import FlagIcon from '@/assets/images/flag.svg';
import CallIcon from '@/assets/images/call.svg';

export default {
    components: { Logo, SidebarItem, PollIcon, GroupIcon, FlagIcon, CallIcon }
}
</script>