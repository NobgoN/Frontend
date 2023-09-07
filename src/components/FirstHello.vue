<script setup>
    const props = defineProps({
        message: String,
        name: {type: String, default: 'jane'},
        
    });
</script>

<template>
    Hello
    <p> {{ props.message }} {{ props.name }}</p>
</template>