<template>
    <div>
      <h1>Nested Conditional Rendering</h1>
      <p v-if="isLoggedIn">
        <span v-if="role === 'admin'">Halo Admin, selamat datang kembali!</span>
        <span v-else-if="role === 'user'">Halo Pengguna, terima kasih telah login.</span>
        <span v-else>Halo, status Anda tidak diketahui.</span>
      </p>
      <p v-else>Silakan login terlebih dahulu.</p>
  
      <button @click="toggleLogin">{{ isLoggedIn ? "Logout" : "Login" }}</button>
      <select v-if="isLoggedIn" v-model="role">
        <option value="admin">Admin</option>
        <option value="user">User</option>
        <option value="">Unknown</option>
      </select>
    </div>
  </template>
  
  <script>
  export default {
    name: 'NestedIfExample',
    data() {
      return {
        isLoggedIn: false,
        role: '',
      };
    },
    methods: {
      toggleLogin() {
        this.isLoggedIn = !this.isLoggedIn;
        if (!this.isLoggedIn) {
          this.role = ''; // Reset role ketika logout
        }
      }
    }
  }
  </script>
  
  <style>
  h1 {
    margin-bottom: 20px;
  }
  </style>
  