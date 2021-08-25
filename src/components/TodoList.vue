<template>
  <div class="container">
    <h2>Todo List</h2>
    <div class="d-flex">
      <input 
        type="text"  
        class="form-control" 
        placeholder="Add a new task here" 
        v-model="inputValue" 
        @keypress.enter="addTask">
      <button 
        class="btn btn-warning" 
        @click="addTask"
        >Add</button>
    </div>
    <div >
      <ul class="list-group mt-3">
        <li 
          class="list-group-item" 
          v-for="(task, index) in tasks" 
          :key="index">
            <div class="d-flex justify-content-between">
              <span>{{index+1}} . {{task.title}}</span>
              <button class="btn btn-danger" 
                @click="removeTask(index)"
              >Remove</button>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TodoList',
  props: {
    msg: String
  },
  data() {
    return {
      inputValue:'',
      tasks:[
        {
          title: 'To throw out the trash',
          id: '1'
        },
        {
          title: 'Feed the dog',
          id: '2'
        }
      ]
    }
  },
  methods: {
    addTask(){
      if(this.inputValue===''){return};
      this.tasks.push({
        title:this.inputValue,
        id: new Date().valueOf()
      }),
      this.inputValue=''

    },
    removeTask(index){
      this.tasks.splice(index,1);
    }
  },
}
</script>
