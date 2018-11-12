<template>
    <div>
        <input type="text" class="todo-input" 
        placeholder="what needs to be done" 
        v-model="newTodo"
        @keyup.enter="addTodo">
        <div v-for="todo of todos" :key="todo.id" class="todo-item">
           {{ todo.title}}
        </div>
    </div>
</template>

<script>
export default {
  name: 'TodoList',
  props: {
    msg: String
  },
  data(){
      return{
          newTodo:"",
          idForTodo: 3,
          todos:[
              //it is a good idea to have an idea --get it from DB
              {
                  "id": 1,
                  "title": "Finish Vue Screencast",
                  "completed":false
              },

              {
                  "id": 2,
                  "title": "Take over world",
                  "completed":false
              }
          ]
      }
  },

  methods:{
      addTodo(){

          if(this.newTodo.trim().length==0) return
          this.todos.push({
              id: this.idForTodo,
              title: this.newTodo,
              completed: false
          })

          this.newTodo=''
          this.idForTodo++
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss">
    .todo-input{
        width: 100%;
        padding: 10px 18px;
        font-size: 18px;
        margin-bottom: 16px;

        &:focus {
            outline: 0;
        }
    }
</style>
