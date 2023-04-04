<template>
    <div class="checkbox" :style="{backgroundColor: color}">
        <div>
            <input 
            type="checkbox" 
            id="checkbox" 
            v-model="checked"  
            @change="heChecked"
            
            
            />
            <label for="checkbox"
             :class="{checkedClass: checked }"
             
             >{{task.body }}</label>
        </div>
        <my-select @selected="changePriority">
            
        </my-select>
        <div class="post__btns">
            <my-button
            @click="$emit('remove', post)"
            >Delete</my-button>
        </div>
    </div>
</template>

<script>
export default {
    data () {
        return {
            checked: "",
            color: "",
            priority: 0
        }
    },
    props: {
        task: {
            type: Object,
            required: true
        }
    },
    methods: {
       heChecked (){
        
        this.task.checked = this.checked;
        this.$emit('checked', this.task);
        
       },
       changePriority (color, priority) {
        this.color = color;
        if(priority === 'High'){
            this.task.priority = 1
        }else if (priority === 'Midl'){
            this.task.priority = 2
        }else{
            this.task.priority = 3
        }
        this.$emit('changePrior', this.task)
       }
    }
}
</script>

<style scoped>
.checkbox {
  padding: 10px;
  border: 2px solid teal;
  margin-top: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 20px;
}
#checkbox {
    margin-right: 10px;
}
.checkedClass {
    text-decoration: line-through;
    
}
</style>