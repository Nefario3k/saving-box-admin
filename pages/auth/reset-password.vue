<template>
  <div style="overflow: hidden" class="relative row auth-page-container">
    <StatusTile
      :absolute="true"
      :border="true"
      :svg="false"
      borderColor="var(--primary-color)"
      :top="14"
      :right="TokenStatusRight"
      color="#EBF4EB"
      subtext="Token has been sent to your email"
      subtextColor="var(--primary-color)"
      :index="33"
    />
    <StatusTile
      :absolute="true"
      :border="false"
      borderColor="red"
      :top="21"
      :right="statusRight"
      color="var(--green)"
      header="Success!"
      headerColor="#fff"
      subtext="New Password Created Successfully"
      subtextColor="#fff"
      :svg="true"
      svgStroke="var(--label-third-color)"
      svgColor="#FFD15D"
      :index="33"
    />
    <div
      class="left auth__image forgot__page col-12 col-md-6 col-lg-6 col-xl-6"
    >
      <img v-if="formStep === 1" src="/images/auth/forgot.png" alt="" />
      <img v-if="formStep === 2" src="/images/auth/confirmP.png" alt="" />
      <img v-if="formStep === 3" src="/images/auth/newPassword.png" alt="" />
      <!-- <div class="auth-page-left-side-overlay">
        <h1 class='notAuthH1' style="color: white; font-size: 30px">SAVINGSBOX</h1>
      </div> -->
    </div>
    <div class="right auth-page col-12 col-md-6 col-lg-6 col-xl-6">
      <div>
        <!-- reset password step one -->
        <section v-if="formStep === 1">
          <!-- header  -->
          <div class="auth-page-header resetPHeader">
            <div class="imgTag noLogo">
              <nuxt-link to="/">
                <img src="/images/logo.png" alt="" />
                <span>SavingsBox</span>
              </nuxt-link>
            </div>
            <h1 class="notAuthH1">Forgot Password</h1>
            <p class="notAuthP">
              Enter the email or Phone Number you registered with.
            </p>
          </div>
          <!-- form  -->
          <form @submit.prevent="nextStep(1)" class="auth-form">
            <div class="row align-items-center">
              <div class="col-12 mb-3" style="position: relative">
                <label for="emailAddress" class="form-label label-design"
                  >Email Address</label
                >
                <input
                  type="email"
                  required
                  class="form-control input-design"
                  id="emailAddress"
                  placeholder="name@example.com"
                />
                <a href="" class="input-top-righ">Use Phone Number</a>
              </div>
              <div class="col-md-6 mb-3">
                <button type="submit" class="btn btn-primary btn-design verify">
                  Send Token
                </button>
              </div>
            </div>
          </form>
        </section>
        <!-- reset password step twu -->

        <section v-if="formStep === 2">
          <!-- header  -->
          <div class="auth-page-header resetPHeader">
            <div class="imgTag noLogo">
              <nuxt-link to="/">
                <img src="/images/logo.png" alt="" />
                <span>SavingsBox</span>
              </nuxt-link>
            </div>
            <h1 class="notAuthH1">Confirm Token</h1>
            <p class="notAuthP">Enter the token sent to your email or phone</p>
          </div>
          <div class="switch-token-method">
            <p>
              A 4-digit token was sent to your email
              <strong>bdmichael.ajayi@gmail.com</strong>
            </p>
            <a href="" @click.prevent="formStep = 1">Send to Phone instead</a>
          </div>
          <!-- token  -->
          <div class="auth-form">
            <div class="row">
              <div class="col-12 py-0">
                <div class="control__form otp__form">
                  <v-otp-input type="number" length="4"></v-otp-input>
                </div>
              </div>
            </div>
            <div class="row">
              <div class="col-12 py-0">
                <div class="control__form">
                  <div
                    class="d-flex justify-content-start resend-token-container"
                  >
                    <span>Didn’t get code?</span>
                    <a href="">Resend Code</a>
                  </div>
                </div>
              </div>
            </div>
            <div class="row">
              <div class="col-12 py-0" style="margin-top: 40px">
                <div class="control__form">
                  <button
                    @click.prevent="formStep = 3"
                    class="btn btn-primary btn-design verify"
                    type="submit"
                  >
                    Confirm
                  </button>
                </div>
              </div>
            </div>
          </div>
        </section>
        <!-- reset password step there -->
        <section v-if="formStep == 3">
          <div class="auth-page-header m-0">
            <div class="imgTag noLogo">
              <nuxt-link to="/">
                <img src="/images/logo.png" alt="" />
                <span>SavingsBox</span>
              </nuxt-link>
            </div>
            <h1 class="notAuthH1">Create New Password</h1>
            <p class="notAuthP">Enter new password</p>
          </div>
          <form @submit.prevent="nextStep(3)" class="auth-form">
            <div class="row align-items-center">
              <div class="col-12" style="position: relative">
                <label for="password" class="form-label label-design"
                  >Password</label
                >
                <div class="relative passwordAdminInput">
                  <input
                    :type="passwordType"
                    class="form-control input-design"
                    id="password"
                    required
                    placeholder="************"
                    v-model="password"
                    @input="checkPasswordStrength"
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
                <div class="passwordStrength">
                  <span class="passwordStrength__text">
                    Password must at least contain
                    <span class="danger">8 characters</span>,
                    <span class="danger">a number</span>,
                    <span class="danger"> an uppercase </span> and
                    <span class="danger">a special character</span>.
                  </span>

                  <div class="passwordStrength__progress">
                    <v-progress-linear
                      v-for="(item, index) in passwordStrength"
                      :key="index"
                      :rounded="true"
                      :height="3"
                      color="var(--green5)"
                      background-color="var(--card-seven)"
                      v-model="item.value"
                    ></v-progress-linear>
                  </div>
                </div>
                <p class="password__strength__indicator">
                  {{ passwordIndicator }}
                </p>
              </div>
              <div class="col-12" style="position: relative">
                <label for="confirmPassword" class="form-label label-design"
                  >Confirm Password</label
                >
                <div class="relative passwordAdminInput">
                  <input
                    :type="confirmPasswordType"
                    class="form-control input-design"
                    id="confirmPassword"
                    required
                    placeholder="************"
                  />
                  <div
                    title="Toggle password view"
                    @click="toggleConfirmPassword"
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
              <div class="col-12">
                <button class="btn btn-primary btn-design verify" type="submit">
                  Create Password
                </button>
              </div>
            </div>
          </form>
        </section>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  layout: "auth",
  data() {
    return {
      formStep: 1,
      password: "",
      passwordType: "password",
      confirmPasswordType: "password",
      passwordIndicator: "Poor",
      statusRight: -500,
      TokenStatusRight: -500,
      passwordStrength: [
        {
          title: "Poor",
          value: 0,
        },
        {
          title: "Medium",
          value: 0,
        },
        {
          title: "Strong",
          value: 0,
        },
      ],
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
    toggleConfirmPassword() {
      if (this.confirmPasswordType == "password") {
        this.confirmPasswordType = "text";
      } else {
        this.confirmPasswordType = "password";
      }
    },
    checkPasswordStrength() {
      const regexWeak =
        /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[!@#$%^&*])[a-zA-Z\d!@#$%^&*]{8,}$/; // Match only numbers with at most 6 characters
      const regexMedium =
        /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[!@#$%^&*])[a-zA-Z\d!@#$%^&*]{8,11}$/; // Match lowercase, uppercase, and numbers with at least 8 characters
      const regexStrong =
        /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[!@#$%^&*])[a-zA-Z\d!@#$%^&*]{12,}$/; // Match lowercase, uppercase, numbers, and special characters with at least 8 characters
      if (this.password.match(regexStrong)) {
        this.passwordStrength[0].value = 100;
        this.passwordStrength[1].value = 100;
        this.passwordStrength[2].value = 100;
        this.passwordIndicator = this.passwordStrength[2].title;
        console.log("1 if");
      } else if (this.password.match(regexMedium)) {
        this.passwordStrength[0].value = 100;
        this.passwordStrength[1].value = 100;
        this.passwordStrength[2].value = 0;
        this.passwordIndicator = this.passwordStrength[1].title;
        console.log("2 if");
      } else if (this.password.match(regexWeak)) {
        this.passwordStrength[0].value = 100;
        this.passwordStrength[1].value = 0;
        this.passwordStrength[2].value = 0;
        this.passwordIndicator = this.passwordStrength[0].title;
        console.log("3 if");
      } else {
        this.passwordStrength[0].value = 0;
        this.passwordStrength[1].value = 0;
        this.passwordStrength[2].value = 0;
        this.passwordIndicator = this.passwordStrength[0].title;
        console.log("else");
      }
    },
    nextStep(type) {
      switch (type) {
        case 1:
          this.TokenStatusRight = 27;
          setTimeout(() => {
            this.TokenStatusRight = -500;
            this.formStep = 2;
          }, 2000);
          break;
        case 3:
          this.statusRight = 5;
          setTimeout(() => {
            this.statusRight = -500;
            window.location.href = "/auth/login";
          }, 2000);
          break;

        default:
          break;
      }
    },
  },
};
</script>