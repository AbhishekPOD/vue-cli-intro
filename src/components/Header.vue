<template>
    <header>
        <h1> {{ title }} </h1>
        <Button @b-click="isModalVisible = true" title="Add Task" bgcolor="green"></Button>
        <Modal 
            :isVisible="isModalVisible"
            @add-task="addTask"
            @close="isModalVisible = false" 
        />
    </header>
</template>

<script>
import Button from './Button.vue';
import Modal from './Modal.vue';

export default {
    name: 'Header',
    data () {
        return {
            isModalVisible: false
        }
    },
    props: ['title'],
    components: {
        Button,
        Modal
    },
    methods: {
        addTask (task) {
            this.$emit('add-task', task)
        }
    },
}
</script>

<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>