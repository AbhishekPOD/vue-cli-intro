<template>
    <div class="modal" v-if="isVisible">
      <div class="modal-content">
        <span class="close" @click="closeModal">&times;</span>
        <h2>Add Task</h2>
        <input type="text" v-model="task" placeholder="Enter new task" />
        <button @click="submitTask">Submit</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
        isVisible: Boolean
    },
    data () {
      return {
        task: '',
      }
    },
    methods: {
      closeModal() {
        this.$emit('close');
      },
      submitTask() {
        if (this.task.trim() !== '') {
          this.$emit('add-task', this.task);
          this.task = '';
          this.closeModal();
        }
      },
    },
  };
  </script>
  
  <style>
  .modal {
    display: block;
    position: fixed;
    z-index: 1;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgb(0, 0, 0);
    background-color: rgba(0, 0, 0, 0.4);
  }
  .modal-content {
    background-color: #fefefe;
    margin: 15% auto;
    padding: 20px;
    border: 1px solid #888;
    width: 80%;
  }
  .close {
    color: #aaa;
    float: right;
    font-size: 28px;
    font-weight: bold;
  }
  .close:hover,
  .close:focus {
    color: black;
    text-decoration: none;
    cursor: pointer;
  }
  </style>
  