<script setup>
    import SnsSidebar from './Parts/SnsSidebar.vue';
</script>

<template>
    <SnsSidebar />
    <div>
        <h2>テストページ1</h2>
        <router-link to="/second">次のページ</router-link>
    </div>
    
</template>