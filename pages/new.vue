<template>
    <div class="container">
      <h1>Create Task</h1>
      <form @submit.prevent="createTask" class="form">
        <div class="form-group">
          <label for="title">Task Title:</label>
          <input type="text" id="title" v-model="title" required class="input-field" />
        </div>
        <div class="form-group">
          <label for="description"> Task Description:</label>
          <textarea id="description" v-model="description" required class="input-field"></textarea>
        </div>
        <div class="form-group">
          <label for="status">Status of Task:</label>
          <select id="status" v-model="status" class="input-field">
            <option value="Not Started">Not Started</option>
            <option value="In Progress">In Progress</option>
            <option value="Completed">Completed</option>
          </select>
        </div>
        <button type="submit" class="btn-create">Create Task</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        title: '',
        description: '',
        status: 'not started'
      };
    },
    methods: {
      createTask() {
  fetch('https://jsonplaceholder.typicode.com/todos', {
    method: 'POST',
    body: JSON.stringify({
      title: this.title,
      description: this.description,
      status: this.status
    }),
    headers: {
      'Content-type': 'application/json; charset=UTF-8',
    },
  })
    .then(response => {
      if (!response.ok) {
        throw new Error('Network response was not ok');
      }
      return response.json();
    })
    .then(json => {
      console.log('Task created successfully:', json);
      this.title = '';
      this.description = '';
      this.status = 'not started';
    })
    .catch(error => {
      console.error('Error creating task:', error);
    });
}

    }
  };
  </script>
  
  <style scoped>
  .container {
    max-width: 500px;
    margin: 0 auto;
  }
  
  .form {
    background-color: #282727b9;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  
  .form-group {
    margin-bottom: 20px;
  }
  
  label {
    font-weight: bold;
  }
  
  .input-field {
    width: 90%;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .btn-create {
    background-color: #11460c;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .btn-create:hover {
    background-color: #0f4d0ac1;
  }
  </style>
  