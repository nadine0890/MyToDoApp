<template>
  <div class="navbar">
    <h1>This is my navbar!</h1>
    <RouterLink to="/">MyData</RouterLink>
    <RouterLink to="/auth">Sign</RouterLink>
    
    <div id="navbar">
      <a href="#" class="active">My Data</a>
      <a href="#">My Lists</a>
      <a href="#">My Tasks</a>
      <button id="userButton2" @click="$router.push('/auth')">Sign Up/Sign In</button>
    </div>
    </div>
</template>

<script>
import { RouterLink } from 'vue-router';
export default {
    name: 'NavBar',
    components: {
      RouterLink,
    }

}
function showLoginModal() {
    alert("Show sign-up/sign-in modal dialog");
  }
  
  function showLogoutButton() {
    var userButton = document.getElementById("userButton2");
    userButton.innerHTML = '<button id="logoutButton">Log Out</button>';
    
    document.getElementById("logoutButton").addEventListener("click", function() {
      alert("Log out button clicked");
      userButton.innerHTML = '';
    });
  }
  
  
    var isLoggedIn = false; 
    if (isLoggedIn) {
      showLogoutButton();
    } else {
      //document.getElementById("userButton2").innerHTML = '<button id="userButton2">Sign Up/Sign In</button>';
      //document.getElementById("loginButton").addEventListener("click", showLoginModal);
    }  
  
</script>

<style scoped>
#navbar {
    background-color: #01394b;
    overflow: hidden;
  }
  
  #navbar a {
    float: left;
    color: white;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
    font-size: 17px;
  }
  
  #navbar a.active {
    background-color: #0185b1;
  }
  
  #navbar button {
    float: right;
    margin-top: 10px;
    margin-right: 20px;
    padding: 10px 20px;
    background-color: #0185b1;
    border: none;
    border-radius: 5px;
    color: white;
    font-size: 16px;
    cursor: pointer;
  }
  
  #navbar2 button:hover {
    background-color: #0185b1;
  }

  #navbar2 {
    background-color: #01394b;
    overflow: hidden;
  }
  
  #navbar2 a {
    float: left;
    color: white;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
    font-size: 17px;
  }
  
  #navbar2 a.active {
    background-color: #0185b1;
  }
  
  #navbar2 #userButton2 {
    float: right;
    margin-top: 10px;
    margin-right: 20px;
    font-size: 16px;
    color: white;
  }
  
  #navbar2 #userButton2 button {
    background-color: #0185b1;
    border: none;
    border-radius: 5px;
    padding: 10px 20px;
    color: white;
    cursor: pointer;
  }
  
  #navbar2 #userButton2 button:hover {
    background-color: #0185b1;
  }
</style>