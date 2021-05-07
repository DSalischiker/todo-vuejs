<template>
    <div>
        <ul>
            <Task v-for="task in tasks" :key="task.id" :task="task" />
        </ul>
    </div>
</template>

<script>
import Task from '@/components/Task.vue';
export default {
    name: 'Tasks',
    props: ['tasks'],
    data(){
        return{

        }
    },
    components: {
        Task,
    }
}
</script>

<style lang="scss" scoped>

</style>