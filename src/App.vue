<template>
 <div class="">
      <h1 class="text-danger text-center
      bg-info p-2">
      {{title}} To Do List
      </h1>
      <div class="container">
      <div class="row mt-3">
      <div class="col">
      <input type="text" class="form-control" v-model="addTasks" v-on:keyup.enter="addInTasks()">
      </div>
      <div class="col">
      <button type="button"  class="btn btn-warning" v-on:click="addInTasks()">Add</button>
      </div>
     
      </div>
      <div class="row">
       <div class="col mb-3">Tasks</div>
       <div class="col-2 mb-3">Done</div>
      </div>
          <div class="" v-if="filterTask.length > 0">
              <div class="row" v-for="(task,index) in filterTask" :key="index">
            <div class="col mb-3" :class="task.done ? 'delete' : '' ">{{task.action}}</div>
                  <div class="col-2 mb-3">
                  <input type="checkbox" v-model="task.done "></div>
              </div>
          </div>
          <div class="alert alert-info" v-else>There is no data</div>
        
          <div class="text-white bg-danger text-center p-2 row ">
          <h5 class="col">Hide Complete</h5>
          
          <input type="checkbox" name="" v-model="hideCompleted" class="col" id="">
          
          </div>
      </div>
  </div>
  
</template>

<script>


export default {
  name: 'App',
  data:  () => ({
    title : 'My Monthly',
    tasks :[],
    hideCompleted : false,
    addTasks : '',
  }),
  //methods  always return 
  computed : {
    filterTask(){
      return this.hideCompleted ? this.tasks.filter((v)=>!v.done) :this.tasks;
    }
  },
    methods :{
      addInTasks(){
       if(this.addTasks === ''){
        return alert('please add task')
       }
       this.tasks.push({
        action: this.addTasks,done: false,
       });
       this.addTasks = '';
      }
    }
}
</script>

<style>
.delete {
  text-decoration: line-through;
}
</style>
