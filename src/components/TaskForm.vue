<template>
    <form @submit.prevent>
      <h4>Create a list</h4>
      <input
       v-model="task.body"
       class="input" 
       type="text" 
       placeholder="Enter your task">
      <my-button class="btn btn_create" @click="createTask" >Create</my-button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            task:{
                body: "",
                checked: false,
                priority: 0
            }
        }
    },
    methods: {
        createTask(){
            this.task.id = Date.now();  
            this.task.priority = 0;
            this.$emit('create', this.task);
            this.task = {
                body: ''
            }
        }
    }
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
}
.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}


</style>