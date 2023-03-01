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
            <h1 class="">Create New User of Month</h1>
            <p>Create a new top user</p>
          </div>

          <section class="input__area update-form">
            <div class="row">
              <!-- fname  -->
              <div class="col-12">
                <label for="adminFname" class="form-label label-design"
                  >First Name</label
                >
                <input
                  type="text"
                  class="form-control input-design"
                  id="adminFname"
                  placeholder="First name"
                />
              </div>
              <!-- lname  -->
              <div class="col-12">
                <label for="adminLname" class="form-label label-design"
                  >Last Name</label
                >
                <input
                  type="text"
                  class="form-control input-design"
                  id="adminLname"
                  placeholder="Last name"
                />
              </div>
              <!-- Occupation  -->
              <div class="col-12">
                <label for="occupation" class="form-label label-design"
                  >Occupation</label
                >
                <input
                  type="text"
                  class="form-control input-design"
                  id="occupation"
                  placeholder="e.g: trader"
                />
              </div>
              <!-- Description/About  -->
              <div class="col-12">
                <label for="desc" class="form-label label-design"
                  >Description/About</label
                >
                <textarea
                  id="desc"
                  class="input-design-textarea shortArea"
                  placeholder="Enter Description here"
                  name=""
                ></textarea>
              </div>
              <!-- Cover Image  -->
              <div class="col-12">
                <label for="coverImage" class="form-label label-design"
                  >User Image</label
                >
                <div class="relative coverImageWrapper">
                  <input
                    type="text"
                    disabled
                    class="form-control input-design"
                    id="coverImage"
                    placeholder="Upload user image here"
                  />
                  <div class="absolute accessIcon">
                    <svg
                      width="24"
                      height="24"
                      viewBox="0 0 24 24"
                      fill="none"
                      xmlns="http://www.w3.org/2000/svg"
                    >
                      <path
                        fill-rule="evenodd"
                        clip-rule="evenodd"
                        d="M7.368 8.79442C7.782 8.79442 8.118 9.13042 8.118 9.54442C8.118 9.95842 7.782 10.2944 7.368 10.2944H6.435C4.816 10.2944 3.5 11.6104 3.5 13.2284V18.1034C3.5 19.7224 4.816 21.0384 6.435 21.0384H17.565C19.183 21.0384 20.5 19.7224 20.5 18.1034V13.2194C20.5 11.6064 19.188 10.2944 17.576 10.2944H16.633C16.219 10.2944 15.883 9.95842 15.883 9.54442C15.883 9.13042 16.219 8.79442 16.633 8.79442H17.576C20.015 8.79442 22 10.7794 22 13.2194V18.1034C22 20.5494 20.01 22.5384 17.565 22.5384H6.435C3.99 22.5384 2 20.5494 2 18.1034V13.2284C2 10.7834 3.99 8.79442 6.435 8.79442H7.368ZM12.5306 2.22202L15.4466 5.15002C15.7386 5.44402 15.7376 5.91802 15.4446 6.21002C15.1506 6.50202 14.6766 6.50202 14.3846 6.20802L12.749 4.56677L12.7496 15.5413H11.2496L11.249 4.56677L9.6156 6.20802C9.4696 6.35602 9.2766 6.42902 9.0846 6.42902C8.8936 6.42902 8.7016 6.35602 8.5556 6.21002C8.2626 5.91802 8.2606 5.44402 8.5536 5.15002L11.4686 2.22202C11.7496 1.93902 12.2496 1.93902 12.5306 2.22202Z"
                        fill="#999C9F"
                      />
                    </svg>
                  </div>
                </div>
              </div>
              <div class="col-12">
                <v-checkbox
                  label="Make User of the month"
                  color="var(--primary-color)"
                  hide-details
                ></v-checkbox>
              </div>
              <div style="margin-top: 130px" class="col-12">
                <button
                  @click="showSuccess = !showSuccess"
                  class="btn btn-primary btn-design"
                >
                  Create
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

            <h1 class="">Created Successfully</h1>
            <p
              style="
                margin: 0 auto !important;
                width: 85%;
                font-size: 1.8rem;
                color: var(--label-color);
              "
            >
              User of the month has been created successfully.
            </p>
          </div>
          <section class="input__area update-form">
            <div class="row">
              <div style="margin-top: 76px" class="pt-0 col-12">
                <button
                  @click="
                    () => {
                      (showDrawer = false), (showSuccess = false);
                    }
                  "
                  class="btn btn-primary btn-design"
                >
                  Close
                </button>
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
.col-12 {
  padding-top: 0;
  // padding-bottom: 0;
}
</style>
