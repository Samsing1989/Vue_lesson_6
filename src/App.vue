<template>
    <div><task-one /></div>
    <div><task-two /></div>
    <div><task-three /></div>
    <div><task-four /></div>
    <div><task-five /></div>
    <div><task-six /></div>
</template>

<script>
import TaskOne from '@/components/TaskOne/index.vue'
import TaskTwo from '@/components/TaskTwo/index.vue'
import TaskThree from '@/components/TaskThree/index.vue'
import TaskFour from '@/components/TaskFour/index.vue'
import TaskFive from '@/components/TaskFive/index.vue'
import TaskSix from '@/components/TaskSix/index.vue'
export default {
    name: 'App',
    components: { TaskOne, TaskTwo, TaskThree, TaskFour, TaskFive, TaskSix },
}
</script>

<style lang="scss">
#app {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
}
</style>
