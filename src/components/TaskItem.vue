<template>
 <div class="task" v-bind:class="{completed: task.completed}">
    <h2>{{ task.title }}</h2>
    <button class="btn btn-done" v-if="!task.completed" v-on:click="completedTask"><i class="fas fa-check"></i></button>
    <button class="btn btn-remove" v-if="task.completed" v-on:click="removeTask"><i class="fas fa-trash"></i></button>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: ['task'],
  methods:{
      completedTask(){
          this.$emit('completedClicked', this.task.id)
      },
      removeTask(){
          this.$emit('removedClicked', this.task.id)
      }
  }
}
</script>


<style lang="scss">
.task{
    position: relative;
    border: 1px solid;
    border-radius: 5px;
    width: 320px;
    height: 120px;
    margin-top: 30px;
    background: #fff;
.btn{
    height:25px;
    width:80px;
    border-radius:5px;
    border:none;
    color:#fff;
    font-size: 20px;
    position: absolute;
    bottom: 5px;
    right: 5px;
}
    .btn-done{
        background: #3ED119;
    }
    .btn-remove{
        background: #000;
    }
}
.completed{
    text-decoration: line-through;
    opacity: 0.6;
}
</style>