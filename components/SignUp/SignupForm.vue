<template>
    <div class="signup-form">
      <div class="form-container">
        <h1 class="title">Welcome to, FindMe</h1>
        <p class="subtitle">Please Signup to continue</p>
  
        <form class="form">
          <!-- Username -->
          <div class="form-group">
            <label class="label">Username:</label>
            <input
              type="text"
              placeholder="Username"
              class="input-field"
            />
          </div>
  
          <!-- Mobile Number -->
          <div class="form-group">
            <label class="label">Mobile Number:</label>
            <input
              type="tel"
              placeholder="Mobile Number"
              class="input-field"
            />
          </div>
  
          <!-- Repeat similar structure for other form elements -->
  
          <button type="submit" class="register-button">
            REGISTER
          </button>
        </form>
  
        <p class="signin-text">Click here to SignIn</p>
      </div>
    </div>
  </template>
  
  <script>
  import styles from './SignupForm.scss';
  
  export default {
    name: 'SignupForm',
    data() {
      return {
      
      }
    }
  }
  </script>
  
  <style lang="scss" module>
  @import './SignupForm.scss';
  </style>