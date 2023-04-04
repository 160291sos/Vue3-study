<template>
    <div v-if="tasks.length > 0">
        <task-item  
        v-for="task in tasks"
        :task="task"
        @remove="$emit('remove', task)"
        :key="task.id"
        @checked="checkDone"
        @changePrior="changePrior"
        />
    </div>
    <h2 v-else>
        List of tasks is emty
    </h2>
    
    
</template>

<script>
import TaskItem from "@/components/TaskItem.vue";
export default {
    components:{TaskItem},
    props: {
        tasks: {
            type: Array,
            required: true
        }
    },
    methods: {
        checkDone(data){
            this.$emit('checkStatus', data)
        },
        changePrior(data){
            this.$emit('filterPrior', data)
        }
    }
}
</script>

<style scoped>

</style>