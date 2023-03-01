<template>
  <div class="auth-page-container relative">
    <div class="auth-page">
      <div class="auth-page-header">
        <h1>Two-factor Authentication</h1>
        <p class="twoFA">Set up two-factor authentication</p>
      </div>

      <div class="switch-token-method text-center">
        <p>
          A 4-digit token was sent to your email
          <strong>bdmichael.ajayi@gmail.com</strong>
        </p>
        <a href="">Send to Phone instead</a>
      </div>

      <div class="auth-form">
        <div class="row">
          <div class="col-12 py-0">
            <div class="control__form otp__form">
              <v-otp-input length="4"></v-otp-input>
            </div>
          </div>
        </div>

        <div class="row">
          <div class="col-12 py-0">
            <div class="control__form">
              <div class="d-flex justify-content-center resend-token-container">
                <span>Didn’t get code?</span>
                <a href="">Resend Code</a>
              </div>
            </div>
          </div>
        </div>

        <div class="row">
          <div class="col-12 py-0" style="margin-top: 40px">
            <div class="control__form">
              <button class="btn btn-primary btn-design" type="submit">
                Confirm
              </button>
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
    return {};
  },
  // page properties go here
};
</script>