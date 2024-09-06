<!-- <script>
import { ref } from "vue";
export default {
  setup() {
    const name = ref('John Doe');
    const status = ref('active');
    const tasks = ref(["Task One", "Task Two", "Task Three"]);

    const changeStatus = () => {
      if (status.value === 'active') {
        status.value = "pending"
      } else if (status.value === 'pending') {
        status.value = "active"
      }
      else {
        status.value = "active"
      }
    }

    return {
      name,
      status,
      changeStatus,
      tasks
    }

  },
}
</script> -->

<script setup>
import { ref , onMounted } from "vue";

    const name = ref('John Doe');
    const status = ref('active');
    const tasks = ref(["Task One", "Task Two", "Task Three"]);
   
    const changeStatus = () => {
      if (status.value === 'active') {
        status.value = "pending"
      } else if (status.value === 'pending') {
        status.value = "active"
      }
      else {
        status.value = "active"
      }
    }
// form
    const newTask = ref('jhjkh');
    const addTask = () =>{
      if(newTask.value.trim() !== ''){ 
        tasks.value.push(newTask.value);
        newTask.value=''
      }
    };

    const deleteTask = (index) =>{
      tasks.value.splice(index,1);
    };

    onMounted(async () => {
      try {
        const response =  await fetch('https://jsonplaceholder.typicode.com/todos');
        const data = await response.json();
        tasks.value =  data.map((task)=>task.title);
      } catch (error) {
        console.log('Error');
        
      }
    });
</script>
<template>
  <div>
    <h1>{{ name }}</h1>
    <p v-if="status === 'active'">User is Active</p>
    <p v-else-if="status === 'pending'">User is Pending</p>
    <p v-else>Unknown</p>

    <h3>Tasks</h3>
    <ul>
      <li v-for="(task , index) in tasks" :key="task">
        <span>{{ task }}</span>
        <button @click="deleteTask(index)">X</button>
      </li>
    </ul>


    <!-- <button v-on:click="changeStatus">Change Status</button> -->
    <button @click="changeStatus">Change Status</button>
  </div>
  <div>
    <form @submit.prevent="addTask">
      <label for="">New Task</label>
      <input type="text" name="newTask" v-model="newTask"/>
      <button type="submit">Click me</button>
    </form>
  </div>
</template>