<template>
  <div class="app">
    
    <task-form
      @create="createTask"
      
      />
      
      <task-list 
      :tasks="tasks"
      @remove="removeTask"
      @checkStatus="filterTaskByDone"
      @filterPrior="filterTaskByPrior"
    />
    
    
  </div>
</template>

<script>
import TaskForm from "@/components/TaskForm.vue";
import TaskList from "@/components/TaskList.vue";
import TaskItem from "@/components/TaskItem.vue";
export default {
  components: {
    TaskForm, TaskList, TaskItem
  },
  data() {
    return {
      tasks: []
    }
  },
methods: {
  createTask(task) {
    this.tasks.unshift(task); 
  },
  removeTask(task){
    this.tasks = this.tasks.filter(p => p.id !== task.id)
  },
  filterTaskByDone(data) { 
   this.tasks.forEach(function(task, index){
     if(task.checked){
        this.tasks.push(task);
        this.tasks.splice(index, 1);
       
      }
    }.bind(this));
    
  },
  filterTaskByPrior(data){
    this.tasks.sort((a,b) => a.priority > b.priority ? 1: -1);
  }
}
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 20px;
}


</style>
