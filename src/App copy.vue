<script>
export default {
  data(){
    return {
      name:"John Doe",
      status:'dsf',
      tasks: ["Task One", "Task Two", "Task Three"],
      link: "https://google.com"
    }
  },
  methods:{
    changeStatus(){
      if (this.status ==='active') {
          this.status = "pending"
      }else if (this.status ==='pending') {
          this.status = "active"
      }
      else{
        this.status  = "active"
      }
    }
  }
}
</script>

<template>
  <div>
    <h1>{{ name }}</h1>
    <p v-if="status === 'active'">User is Active</p>
    <p v-else-if="status === 'pending'">User is Pending</p>
    <p v-else>Unknown</p>

    <h3>Tasks</h3>
    <ul>
      <li v-for="task in tasks" :key="task">{{ task }}</li>
    </ul>
    <!-- <a v-bind:href="link">Google</a>    long way of doing this -->
    <a :href="link">Google</a>

    <!-- <button v-on:click="changeStatus">Change Status</button> -->
    <button @click="changeStatus">Change Status</button>
  </div>
</template>