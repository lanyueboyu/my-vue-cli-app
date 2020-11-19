<template>
  <div>
    <div>
        <input v-model="inputValue"/>
        <button @click="handleSubmit">提交</button>
    </div>
    <ul>
        <todo-item 
            v-for="(item, index) of list"
            :key= "index"
            :content= "item"
            :index= "index"
            @delete="handleDelete">
        </todo-item>
    </ul>
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
    components: {
        'todo-item': TodoItem
    },
    // 在vue cli中数据要是函数，返回值为对应的数据
    data: function(){
        return {
            inputValue: '',
            list: []
        }
    },
    // 在es6中的简化写法
    // data () {
    //     return {
    //         inputValue: ''
    //     }
    // }
    methods: {
        handleSubmit: function(){
            this.list.push(this.inputValue)
            this.inputValue = ''
        },
        handleDelete: function(index){
            this.list.splice(index, 1)
        }
    }
};
</script>

<style scoped>
</style>
