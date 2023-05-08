<template>
    <div id="content">
    <h1>My Tasks</h1>

    <div id="addListForm">
      <h2>Add a new item</h2>
      <div>
        <label for="listName">Task Name:</label>
        <input type="text" id="listName" name="listName">
        <button onclick="addList()">Add Task</button>
      </div>
    </div>

    <ul id="todoList">
    </ul>
    </div>
  </template>
  
  <script>
  import { RouterLink } from 'vue-router';
  export default {
      name: 'TasksView',
      components: {
      RouterLink,
    }

  }
  var lists = [
    { id: 1, name: " ", tasks: [] },
    { id: 2, name: " ", tasks: [] },
    { id: 3, name: " ", tasks: [] }
  ];
  
    function addList() {
        var listName = document.getElementById("listName").value;
  
        var newListId = lists.length + 1;
  
        var newList = { id: newListId, name: listName, tasks: [] };
  
        lists.push(newList);
  
        document.getElementById("listName").value = "";
  
    displayLists();
  }
  
    function editList(listId) {
      var list = lists.find(function(item) {
      return item.id === listId;
    });
  
    var newName = prompt("Enter a new name for the list:", list.name);
  
    list.name = newName;
  
    displayLists();
  }
  
  function deleteList(listId) {
    var listIndex = lists.findIndex(function(item) {
      return item.id === listId;
    });
  
    lists.splice(listIndex, 1);
  
    displayLists();
  }
  
  function displayLists() {
    var listElement = document.getElementById("todoList");
    listElement.innerHTML = "";
  }

  </script>
  
  <style>
  #content {
    max-width: 800px;
    margin: 0 auto;
    padding: 20px;
    background-color: #fff;
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
  }
  
  #content h1 {
    font-size: 32px;
    margin-top: 0;
  }
  
  #addListForm {
    margin-bottom: 20px;
  }
  
  #addListForm label {
    font-weight: bold;
    display: block;
    margin-bottom: 10px;
  }
  
  #addListForm input[type="text"] {
    width: 100%;
    padding: 10px;
    margin-bottom: 20px;
    border-radius: 5px;
    border: 1px solid #ccc;
    box-sizing: border-box;
  }
  
  #addListForm button[type="submit"] {
    background-color: #5c0297;
    color: #fff;
    border: none;
    padding: 10px 20px;
    border-radius: 5px;
    cursor: pointer;
  }
  
  #addListForm button[type="submit"]:hover {
    background-color: #5c0297;
  }
  
  .todo-list {
    list-style-type: none;
    margin: 0;
    padding: 0;
  }
  
  .todo-list li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #ccc;
  }
  
  .todo-list li:last-child {
    border-bottom: none;
  }
  
  .todo-list li span {
    font-weight: bold;
    margin-right: 10px;
  }
  
  .todo-list li button {
    background-color: #c99ae9;
    color: #fff;
    border: none;
    padding: 5px 10px;
    border-radius: 5px;
    cursor: pointer;
  }
  
  .todo-list li button:hover {
    background-color: #5c0297;
  }
  </style>