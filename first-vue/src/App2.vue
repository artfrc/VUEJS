<script>
export default {
  data() {
    return {
      name: 'John Due',
      status: 'peding',
      tasks: ['Task One', 'Task Two', 'Task Three'],
      link: 'https://google.com'
    };

  },
  methods: {
    toogleStatus() {
      if(this.status === 'active') this.status = 'peding'
      else if(this.status === 'pending') this.status = 'inactive'
      else this.status = 'active';
    }
  }
};
</script>

<template>
  <h1>{{  name }}</h1>,
  <p v-if=" status === 'active' ">User is active!</p>
  <p v-else-if=" status === 'peding'">User is peding</p>
  <p v-else>User is inactive</p> <br>
  <h2>Tasks:</h2> <br>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul> <br>
  <a :href="link">CLick for Google</a> <br>

<button @click="toogleStatus">Change Status</button>
</template>
