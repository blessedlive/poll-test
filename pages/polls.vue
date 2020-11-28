<template>
    <div class="page-container">
        <PollNavbar/>
        <NuxtChild  /> 
    </div> 
</template>

<script>
import PollNavbar from '@/components/Poll/PollNavbar';

export default {
    components: { PollNavbar },
    created() {
        this.$router.replace({ path: '/polls/settings' });
    }
}
</script>