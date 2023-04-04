<template>
<div class="select" >
  <select v-model="selected" 
        @change="changePriority"    
        :style="{backgroundColor: this.style[this.selected]}"
        >
    <option disabled value="">Select priority</option>
    <option>High</option>
    <option>Midl</option>
    <option>Low</option>
  </select>
</div>
</template>

<script>
import { removeDotSegments } from 'uri-js';

export default {
    name: 'my-select',
    data (){
        return {
            selected: '',
            style: {
                High: 'tomato',
                Midl: 'goldenrod',
                Low: 'lightblue'
            }
        }
    },
    methods: {
        changePriority (){
            this.$emit('selected', this.style[this.selected], this.selected)
        }
    }
}
</script>

<style scoped>
select {
    font-size: 15px;
    padding: 10px 15px;
    border: none;
}
</style>