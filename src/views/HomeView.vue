<template>
  <div class="home">
      <h3>Vue TO DO LIST</h3>
      <form>
        <input type="text" name="task" id="task" placeholder="Add a new task" v-model.lazy.trim="task">
        <button @click.prevent="addTask">+</button>
      </form>
      <div v-for="(t,index) in taskList" :key="index">
          <input type="checkbox" name="taskdone" id="taskdone">
          <span>{{t}}</span>
          <button @click.prevent="deleteTask(t)">Delete</button>
      </div>
       
  </div>
</template>

<script>


export default {
  name: 'HomeView',
  data (){
    return {
        taskList : [ 
          
        ],
        task : ''
    }
  },
  methods: {
     addTask(){
        if(this.taskList.indexOf(this.task) === -1 && this.task !==''){
           this.taskList.push(this.task)
        }
        this.task = ''
     },
     deleteTask(t){
         this.taskList.splice(t,1)
     }
  },
  watch : {
     taskList: {
       handler(newVal){
          localStorage.setItem('taskList',JSON.stringify(newVal))
       },
       deep: true
     }
  },
  mounted(){
    this.taskList = JSON.parse(localStorage.getItem("taskList")) || []
  }
  }

</script>
<style>
.home{
    display: inline-block;
    background-color:rgba(255,255,255,0.3);
    padding: 10px;
    color: #222;
    overflow: auto;
    border-radius:15px;
}
form input{
  width: 250px;
  margin: 5px 2px 7px 2px;
  height: 20px;
  background:none;
  outline: none;
  border: none;
  padding: 2px;
  border-bottom: 1px solid black;
  box-shadow: none;
}
.home div{
  width: 100%;
  height: 30px;
  border-radius: 15px ;
  margin: 10px 0;
  background: #fff;
  display: flex;
  flex-direction: row;
  justify-content:space-around;
  align-items: center;
}
form button{
  font-weight: 800;
  border: none;
  border-radius:50%;
  position: relative;
  display: inline-block;
  padding: auto;
  color: #fff;
  z-index: 1
}
form button::before{
  content: '';
  width:7px;
  height: 7px;
  background:black;
  display: block;
  padding:3px;
  position: absolute;
  border-radius:50%;
  top:50%;
  left:50%;
  transform: translate(-50%,-50%);
  z-index: -1;
}

#taskdone{
  border-radius:50px ;
}
.home div button{
  border-radius:10px ;
  border: none;
  background-color:rgba(241, 128, 128, 0.413);
  color: #fff
}
#taskdone:checked ~ span{
  text-decoration: line-through;
  text-decoration-color:rgba(235, 39, 39, 0.413) ;
}

</style>
