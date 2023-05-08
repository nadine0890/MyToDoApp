<template>
 <div class="container">
    <div class="card" v-if="!user">
      <h2 class="card-title">Sign In</h2>
      <form @submit.prevent="login" class="card-body">
        <div class="form-group">
          <label for="email">Email</label>
          <input type="email" id="email" v-model="email" class="form-control">
        </div>
        <div class="form-group">
          <label for="password">Password</label>
          <input type="password" id="password" v-model="password" class="form-control">
        </div>
        <button type="submit" class="btn btn-primary" v-if="!isSigningUp">Sign In</button>
        <button type="button" class="btn btn-secondary" v-if="!isSigningUp" @click="isSigningUp = true">Sign Up</button>
        <button type="submit" class="btn btn-primary" v-if="isSigningUp">Sign Up</button>
        <button type="button" class="btn btn-secondary" v-if="isSigningUp" @click="isSigningUp = false">Cancel</button>
      </form>
    </div>
    <div class="card" v-else>
      <h2 class="card-title">Dashboard</h2>
      <div class="card-body">
        <p>Welcome, {{ user.email }}!</p>
        <button @click="logout" class="btn btn-primary">Sign Out</button>
      </div>
    </div>
  </div>
</template>

<script>

export default {
    name: 'AuthView',


data() {
    return {
      email: '',
      password: '',
      isSigningUp: false,
      user: null
    }
  },
  methods: {
    async login() {
      const { user, error } = await supabase.auth.signIn({
        email: this.email,
        password: this.password
      })

      if (error) {
        alert(error.message)
      } else {
        this.user = user
      }
    },
    async signUp() {
      const { user, error } = await supabase.auth.signUp({
        email: this.email,
        password: this.password
      })

      if (error) {
        alert(error.message)
      } else {
        alert('Check your email for verification link.')
        this.isSigningUp = false
      }
    },
    async logout() {
      await supabase.auth.signOut()
      this.user = null
    }
  },
  async mounted() {
    const user = supabase.auth.user()
    if (user) {
      this.user = user
    }
  }
}

</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #f5f5f5;
  font-family: Arial, sans-serif;
}

.card {
  max-width: 500px;
  width: 100%;
  background-color: #fff;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
  padding: 2rem;
  border-radius: 5px;
}

.card-title {
  margin-top: 0;
}

.form-group {
  margin-bottom: 1rem;
}

label {
  display: block;
  margin-bottom: 0.5rem;
  font-weight: bold;
}

input[type="email"],
input[type="password"] {
  width: 100%;
  padding: 0.5rem;
  border-radius: 5px;
  border: 1px solid #ccc;
  font-size: 1rem;
}

.btn {
  padding: 0.5rem 1rem;
  border-radius: 5px;
  font-size: 1rem;
  font-weight: bold;
  text-transform: uppercase;
  cursor: pointer;
}

.btn-primary {
  color: #fff;
  background-color: #0185b1;
  border-color: #0185b1;
  margin-right: 0.5rem;
}

.btn-secondary {
  color: #333;
  background-color: #ccc;
  border-color: #ccc;
}

.btn-primary:hover, .btn-secondary:hover {
  filter: brightness(90%);
}
</style>

