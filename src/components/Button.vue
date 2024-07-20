<template>
    <button :style="{ 'background-color': bgcolor }" @click="$emit('b-click')"> {{ title }}</button>    
</template>

<script>
export default {
    name: 'Button',
    props: {
        title: String,
        bgcolor: String,
    },
}
</script>

<style scoped>

</style>