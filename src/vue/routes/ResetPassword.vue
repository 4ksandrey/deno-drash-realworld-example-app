<template>
  <div class="auth-page">
    <div class="container page">
      <div class="row">
        <div class="col-md-6 offset-md-3 col-xs-12">
          <h1 class="text-xs-center">Reset Password</h1>
          <form @submit.prevent="submit">
            <fieldset class="form-group">
              <input
                class="form-control form-control-lg"
                type="email"
                v-model="email"
                placeholder="Email"
                required
              />
            </fieldset>
            <fieldset class="form-group">
              <input
                class="form-control form-control-lg"
                type="password"
                v-model="password"
                placeholder="New Password"
                required
              />
            </fieldset>
            <fieldset class="form-group">
              <input
                class="form-control form-control-lg"
                type="password"
                v-model="confirmPassword"
                placeholder="Confirm New Password"
                required
              />
            </fieldset>
            <div v-if="error" class="error-messages">
              <li>{{ error }}</li>
            </div>
            <button class="btn btn-lg btn-primary btn-block" type="submit">
              Reset Password
            </button>
          </form>
          <p class="text-xs-center mt-3">
            <router-link :to="{ name: 'login' }">Back to login</router-link>
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ResetPassword",
  data() {
    return {
      email: "",
      password: "",
      confirmPassword: "",
      error: ""
    };
  },
  methods: {
    submit() {
      if (this.password !== this.confirmPassword) {
        this.error = "Passwords do not match.";
        return;
      }

      // Тут можна надіслати запит на бекенд, наприклад:
      // this.$axios.post('/api/reset-password', { email: this.email, password: this.password })

      console.log("Resetting password for:", this.email);
      alert("Password successfully reset!");
      this.$router.push({ name: "login" });
    }
  }
};
</script>