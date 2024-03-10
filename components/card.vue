<template>
    <div>
        <div class="card">
            <div class="topcardbox">
                <span class="heading">Not Started</span><span class="count">{{ notStartedTasks.length }}</span>
                <div class="sidemenu">
            <span>---</span>
            <span class="addnew"> <NuxtLink to="/new">+</NuxtLink> </span>
        </div>
            </div>
            <ul>
              <li v-for="task in notStartedTasks" :key="task.id">{{ task.title }}</li>
            </ul>
            <span class="addnew"> <NuxtLink to="/new">New +</NuxtLink> </span>
        </div>
    </div>
</template>

<!-- <script>
    export default{
        props:['cardname']
    }
</script> -->

<style scoped>
    .topcardbox{
        display: flex;
        align-items: center;
    }

    .card{
        width: 300px;
        margin: .5rem; 
        padding: 1rem;       
    }

    .sidemenu{
        font-weight: bold;
        color: rgba(128, 128, 128, 0.691);
        font-size: larger;
        margin-left: 150px;
    }
    .heading{
        background-color: lightcoral;
        padding: .2rem;
        border-radius: 5px;
    }

    .count{
        margin-left: 0.5rem;
        color: grey;
    }

    ul{
        list-style: none;
        padding: 0;
        margin-top: 1rem;
        font-size: 1.2rem;
        font-weight: bold;
    }

    li{
        padding: .5rem;
        border: 1px solid rgb(56, 53, 53);
        border-radius: 5px;
        color: rgb(62, 61, 61);
        margin-bottom: .5rem;
        box-shadow: 5px 5px 5px 4px  rgba(128, 128, 128, 0.512);
    }

    .addnew{
        font-size: 1.2rem;
        font-weight: bold;
        color: grey;
        padding-left: .5rem;
    }

    a{
        text-decoration: none;
        color: grey;
    }

</style>

<script>
import { ref, onMounted } from 'vue'; // Import ref and onMounted from Vue

export default {
  data() {
    return {
      tasks: []
    };
  },
  setup() {
    const notStartedTasks = ref([]);

    const fetchTasks = async () => {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/todos');
        if (!response.ok) {
          throw new Error('Network response was not ok');
        }
        const data = await response.json();
        notStartedTasks.value = data.filter(task => task.completed === false);
      } catch (error) {
        console.error('Error fetching tasks:', error);
      }
    };

    onMounted(() => {
      fetchTasks();
    });

    return {
      notStartedTasks
    };
  }
};
</script>