<template>
  <div style="position: relative">
    <!-- <v-overlay
      z-index="99"
      :opacity="0.4"
      :value="showDrawer"
      @click="closeDrawer()"
    ></v-overlay> -->
    <v-navigation-drawer
      style="z-index: 100"
      v-model="showDrawer"
      :right="true"
      :width="width"
      temporary
      fixed
      class="adminPanel"
    >
      <!-- create auto savings form -->
      <v-app-bar
        style="margin-left: 1px"
        color="#fff"
        :elevation="elevation"
        fixed
        :height="50"
      >
        <div class="text-right">
          <svg
            @click="closeDrawer()"
            width="30"
            height="30"
            viewBox="0 0 30 30"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              d="M22.5 7.5L7.5 22.5"
              stroke="#FF0000"
              stroke-width="1.5"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
            <path
              d="M7.5 7.5L22.5 22.5"
              stroke="#FF0000"
              stroke-width="1.5"
              stroke-linecap="round"
              stroke-linejoin="round"
            />
          </svg>
        </div>
      </v-app-bar>

      <div
        v-if="!showSuccess"
        ref="myDiv"
        class="mt-2 right-drawer-container"
        @scroll="handleScroll"
      >
        <div>
          <div class="right-drawer-title">
            <h1 class="">Approve Loan Request</h1>
            <p>
              You are about to approve this loan and this action can not be
              reversed
            </p>
          </div>

          <section class="input__area update-form">
            <div class="row">
              <!-- Why do you want to approve this loan?  -->
              <div class="col-12">
                <label for="planTitle" class="form-label label-design"
                  >Why do you want to approve this loan?</label
                >
                <textarea
                  class="input-design-textarea"
                  placeholder="Write Note of approval and what the user need to do"
                  name=""
                  id=""
                ></textarea>
              </div>
              <div class="col-12">
                <p class="amount">Do you wish to continue?</p>
              </div>
              <div style="margin-top: 130px" class="col-12">
                <button
                  @click="showSuccess = !showSuccess"
                  class="btn btn-primary btn-design"
                >
                  Approve
                </button>
              </div>
            </div>
          </section>
        </div>
      </div>
      <div
        v-else
        class="h-75 d-flex justify-content-center align-center mt-2 right-drawer-container text-center"
      >
        <div>
          <div class="right-drawer-title">
            <svg
              class="mb-5"
              width="78"
              height="78"
              viewBox="0 0 78 78"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M29.25 41.4375L36.5625 48.75L48.75 31.6875M68.25 39C68.25 42.8412 67.4934 46.6447 66.0235 50.1935C64.5535 53.7423 62.399 56.9668 59.6829 59.6829C56.9668 62.399 53.7423 64.5535 50.1935 66.0235C46.6447 67.4934 42.8412 68.25 39 68.25C35.1588 68.25 31.3553 67.4934 27.8065 66.0235C24.2577 64.5535 21.0332 62.399 18.3171 59.6829C15.601 56.9668 13.4465 53.7423 11.9765 50.1935C10.5066 46.6447 9.75 42.8412 9.75 39C9.75 31.2424 12.8317 23.8026 18.3171 18.3171C23.8026 12.8317 31.2424 9.75 39 9.75C46.7576 9.75 54.1974 12.8317 59.6829 18.3171C65.1683 23.8026 68.25 31.2424 68.25 39Z"
                stroke="#61CA61"
                stroke-width="2.5"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>

            <h1 class="">Loan Approved</h1>
            <p
              style="
                margin: 0 auto !important;
                width: 95%;
                font-size: 1.8rem;
                color: var(--label-color);
              "
            >
              You have just approved the loan request for this user
              <strong>@johndoe</strong>
            </p>
          </div>
          <section class="input__area update-form">
            <div class="row">
              <div style="margin-top: 37px" class="pt-0 col-12">
                <p @click="closeDrawer()" class="closeDash">
                  Go to loan dashboard
                </p>
              </div>
            </div>
          </section>
        </div>
      </div>
    </v-navigation-drawer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showDrawer: false,
      elevation: 0,
      width: 512,
      showSuccess: false,
    };
  },
  mounted() {
    var nx = window.innerWidth;
    if (nx <= 540) {
      this.width = "100vw";
    }
    window.addEventListener("resize", function (event) {
      var w = window.innerWidth;
      nx = w;
    });
    $(window).resize(() => {
      if (nx <= 540) {
        this.width = "100vw";
      } else {
        this.width = 512;
      }
    });
  },
  methods: {
    closeDrawer() {
      this.showDrawer = false;
    },
    showPanel() {
      this.showDrawer = true;
    },
    handleScroll() {
      const myDiv = this.$refs.myDiv;
      const heightScrolled = myDiv.scrollTop;
      // const initialHeight = myDiv.scrollHeight;
      if (heightScrolled > 0) {
        this.elevation = 2;
      } else {
        this.elevation = 0;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.text-right {
  width: 100%;
  display: flex;
  justify-content: flex-end;
}
.amount {
  // margin: 36px 0 13px;
  margin-bottom: 0;
  font-weight: 400;
  font-size: 1.8rem;
  color: var(--label-third-color);
}
.closeDash {
  color: var(--primary-color);
  font-weight: 500;
  margin: 0;
  font-size: 1.8rem;
  cursor: pointer;
}
</style>
