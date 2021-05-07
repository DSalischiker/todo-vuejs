<template>
    <div>
        <ul>
            <Task
            v-for="(task, $index) in tasks"
            :key="task.id"
            :task="task"
            @deleteTask="deleteTask($index)"
            @finishedTask="finishedTask($index)"/>
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
            /* tasksUnfinished: [],
            tasksFinished: [], */
        }
    },
    components: {
        Task,
    },
    methods: {
        deleteTask(index){
            this.tasks.splice(index, 1);
        },
        finishedTask(index){
            this.tasks[index].finished = true;
        }
    },
    computed: {
        tasksUnfinished() {
           return this.tasks.filter(task => task.finished == false);
        },
        tasksFinished(){
           return this.tasks.filter(task => task.finished == true);
        }
    }
}
</script>

<style lang="scss" scoped>

</style>