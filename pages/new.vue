<template>
    <div class="container">
      <h1>Create Task</h1>
      <form @submit.prevent="createTask" class="form">
        <div class="form-group">
          <label for="title">Title:</label>
          <input type="text" id="title" v-model="title" required class="input-field" />
        </div>
        <div class="form-group">
          <label for="description">Description:</label>
          <textarea id="description" v-model="description" required class="input-field"></textarea>
        </div>
        <div class="form-group">
          <label for="status">Status:</label>
          <select id="status" v-model="status" class="input-field">
            <option value="not started">Not Started</option>
            <option value="in progress">In Progress</option>
            <option value="completed">Completed</option>
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
        console.log('Creating task:', { title: this.title, description: this.description, status: this.status });
        this.title = '';
        this.description = '';
        this.status = 'not started';
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
    background-color: #f9f9f9;
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
    background-color: #007bff;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .btn-create:hover {
    background-color: #0056b3;
  }
  </style>
  