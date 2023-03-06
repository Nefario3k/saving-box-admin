<template>
  <div class="row auth-page-container">
    <div class="left auth-page col-12 col-md-6 col-lg-6 col-xl-6">
      <div>
        <!-- header  -->
        <div class="auth-page-header">
          <div class="imgTag">
            <nuxt-link to="/">
              <img src="/images/logo.png" alt="" />
              <span>SavingsBox</span>
            </nuxt-link>
          </div>

          <p class="loginP">Login</p>
          <span class="subtitle">Login to your account</span>
        </div>
        <form autocomplete="off" class="auth-form">
          <div class="row">
            <div class="col-12 pt-0">
              <div class="control__form">
                <label for="adminEmailAddress" class="form-label label-design"
                  >Email Address</label
                >
                <input
                  autocomplete="off"
                  type="email"
                  class="form-control input-design"
                  id="adminEmailAddress"
                  placeholder="name@example.com"
                />
              </div>
            </div>
            <div class="col-12 py-0">
              <div class="control__form">
                <label for="adminPassword" class="form-label label-design"
                  >Password</label
                >
                <div class="relative passwordAdminInput">
                  <input
                    autocomplete="off"
                    :type="passwordType"
                    class="form-control input-design"
                    id="adminPassword"
                    placeholder="Enter Password"
                  />
                  <div
                    title="Toggle password view"
                    @click="togglePassword"
                    class="absolute passwordToggle"
                  >
                    <svg
                      width="19"
                      height="14"
                      viewBox="0 0 19 14"
                      fill="none"
                      xmlns="http://www.w3.org/2000/svg"
                    >
                      <path
                        d="M17.1849 5.19635C17.8034 5.88868 18.1127 6.23484 18.1127 6.82863C18.1127 7.42243 17.8034 7.76859 17.1849 8.46092C15.6444 10.1852 12.8876 12.6573 9.74295 12.6573C6.59833 12.6573 3.84146 10.1852 2.30101 8.46092C1.6825 7.76859 1.37324 7.42243 1.37324 6.82863C1.37324 6.23484 1.6825 5.88867 2.30101 5.19635C3.84146 3.47207 6.59833 1 9.74295 1C12.8876 1 15.6444 3.47208 17.1849 5.19635Z"
                        stroke="#999C9F"
                        stroke-width="1.55592"
                      />
                      <circle cx="10" cy="7" r="2" fill="#999C9F" />
                    </svg>
                  </div>
                </div>
              </div>
            </div>
            <div style="margin-top: 42px" class="col-12 py-0">
              <div class="control__form">
                <nuxt-link to="/auth/2fa-otp" class="btn btn-primary btn-design"
                  >Login</nuxt-link
                >
              </div>
            </div>
            <div
              style="margin-top: 30px"
              class="col-12 py-0 form-text-section text-center"
            >
              <nuxt-link to="/auth/reset-password">Forgot Password?</nuxt-link>
            </div>
          </div>
        </form>
      </div>
    </div>
    <div
      class="right auth__image login__page col-12 col-md-6 col-lg-6 col-xl-6"
    >
      <img src="/images/auth/login.png" alt="" />
    </div>
  </div>
</template>

<script>
export default {
  layout: "auth",
  data() {
    return {
      passwordType: "password",
    };
  },
  methods: {
    togglePassword() {
      if (this.passwordType == "password") {
        this.passwordType = "text";
      } else {
        this.passwordType = "password";
      }
    },
  },
  // page properties go here
};
</script>