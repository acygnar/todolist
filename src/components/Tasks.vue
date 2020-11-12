<template>
<div class="main">
    <div class="container">
    <input v-on:keyup.enter="addTask()"
           type="text"
           autocomplete="off"
           placeholder="Dodaj zadanie"
           v-model="newTask"
           :class="{'border-red': error}"
           >
    <p class="red" v-if="error">Wpisz treść zadania</p>
    <button v-on:click="addTask()">Dodaj</button>
    </div>
     <transition-group mode="out-in" name="fade">
    <TaskItem v-for="task in tasks"  :key="task.id" :task="task" @completedClicked="completTask" @removedClicked="removeTask"  />
     </transition-group>
</div>
</template>

<script>
import TaskItem from './TaskItem.vue'
export default {
  components:{
      TaskItem,
  },
  name: 'Tasks',
  data(){
      return{
          newTask: '',
          id:0,
          tasks:[],
          error:false,
      }
  },
  methods:{
      addTask(){
          if(this.newTask == ''){
              this.error = true,
              console.log(this.error)
          }
          else{
              this.error = false,
              this.tasks.push({id: this.id++, title: this.newTask, completed: false})
              this.newTask = ""
          }
      },
      completTask(id){
          const index = this.tasks.findIndex(el => el.id === id)
          this.tasks[index].completed = true;
      },
      removeTask(id){
          const index = this.tasks.findIndex(el => el.id === id)
          this.tasks.splice(index, 1)
      },
  }
}
</script>


<style lang="scss" scoped>
.main{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    .container{
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;

    input[type='text']{
        width: 300px;
        height: 10px;
        border: none;
        border-radius: 5px;
        padding: 10px;
    }
    button{
        width:80px;
        height: 25px;
        line-height: 25px;
        text-align: center;
        margin-top: 15px;
        border: none;
        border-radius:5px;
        font-weight: 600;
        font-size: 16px;
        color: #fff;
        background: #2c3e50;
        cursor: pointer;
    }
    }
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
.border-red{
       border: 1px solid red !important;
    }
.red{
    color: red;
    font-size: 14px;
    font-weight: 700;
}
</style>