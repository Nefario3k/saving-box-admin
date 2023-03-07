<template>
  <div class="row auth-page-container relative">
    <StatusTile
      :absolute="true"
      :border="false"
      :svg="false"
      :top="18"
      :right="statusRight"
      color="#F2EDED"
      header="Verified Successfully"
      headerColor="var(--primary-color)"
      subtext="2FA verified successfully"
      subtextColor="var(--black3)"
      svgStroke="var(--label-third-color)"
      :index="33"
    />
    <div class="left auth__image twofa__page col-12 col-md-6 col-lg-6 col-xl-6">
      <img src="/images/auth/twofactor.png" alt="" />
    </div>
    <div class="right auth-page col-12 col-md-6 col-lg-6 col-xl-6">
      <div>
        <!-- header  -->
        <div class="m-0 auth-page-header">
          <div class="imgTag">
            <nuxt-link to="/">
              <img src="/images/logo.png" alt="" />
              <span>SavingsBox</span>
            </nuxt-link>
          </div>
          <h1 class="notAuthH1">Two-factor Authentication</h1>
          <p class="twoFA notAuthP">Verify to secure your account</p>
        </div>
        <!-- token text  -->
        <div class="switch-token-method">
          <p>
            A 4-digit token was sent to your email [
            <strong>bdmichael.ajayi@gmail.com</strong>]
          </p>
          <a href="">Send to Phone instead</a>
        </div>
        <!-- token  -->
        <div class="auth-form">
          <div class="row">
            <div class="col-12 py-0">
              <div class="control__form otp__form">
                <v-otp-input
                  type="number"
                  @finish="login"
                  v-model="tokenNUmber"
                  length="4"
                ></v-otp-input>
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
                  @click="login"
                  :disabled="tokenNUmber.length != 4"
                  class="btn btn-primary btn-design verify"
                  type="submit"
                >
                  Verify
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="absolute verifyAuth"></div>
  </div>
</template>

<script>
export default {
  layout: "auth",
  data() {
    return {
      tokenNUmber: "",
      statusRight: -500,
    };
  },
  methods: {
    login() {
      this.statusRight = 21;
      setTimeout(() => {
        this.statusRight = -500;
        this.tokenNUmber = "";
        window.location.href = "/";
      }, 2000);
    },
  },
};
</script>