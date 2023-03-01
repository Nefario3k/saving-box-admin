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
        ref="myDiv"
        class="mt-2 right-drawer-container"
        @scroll="handleScroll"
      >
        <div>
          <div class="right-drawer-title">
            <h1 class="">Create Jollification Plan</h1>
            <p>Create new jollification plan</p>
          </div>

          <section class="input__area update-form">
            <div class="row">
              <!-- Jollification Title  -->
              <div class="col-12">
                <label for="invertmentTitle" class="form-label label-design"
                  >Jollification Title</label
                >
                <input
                  type="text"
                  class="form-control input-design"
                  id="invertmentTitle"
                  placeholder="Jollification Title"
                />
              </div>
              <!-- Reg, Opens  -->
              <div class="col-6">
                <label for="open" class="form-label label-design"
                  >Reg, Opens</label
                >
                <input
                  type="date"
                  class="form-control input-design"
                  id="open"
                />
              </div>
              <!-- Reg. Closes  -->
              <div class="col-6">
                <label for="close" class="form-label label-design"
                  >Reg. Closes</label
                >
                <input
                  type="date"
                  class="form-control input-design"
                  id="close"
                />
              </div>
              <!-- Period/Duration  -->
              <div class="col-12">
                <label class="form-label label-design">Period/Duration</label>
                <v-menu :nudge-bottom="3" offset-y max-height="190">
                  <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                      <input
                        style="cursor: pointer"
                        type="text"
                        disabled
                        value="11 Months"
                        class="form-control input-design"
                        placeholder="234"
                      />
                      <div class="absolute carret">
                        <svg
                          width="14"
                          height="9"
                          viewBox="0 0 14 9"
                          fill="none"
                          xmlns="http://www.w3.org/2000/svg"
                        >
                          <path
                            d="M13 1L7 7L1 1"
                            stroke="#000831"
                            stroke-width="2"
                            stroke-linecap="round"
                          />
                        </svg>
                      </div>
                    </div>
                  </template>
                  <v-list class="dropdown__list">
                    <v-list-item
                      v-for="n in 8"
                      :key="n"
                      class="dropdown__list-item"
                    >
                      <v-list-item-title class="dropdown__list-title"
                        >11 Months</v-list-item-title
                      >
                    </v-list-item>
                  </v-list>
                </v-menu>
              </div>
              <!-- Description/Rules  -->
              <div class="col-12">
                <label for="desc" class="form-label label-design"
                  >Description/Rules</label
                >
                <textarea
                  class="input-design-textarea shortArea"
                  placeholder="Enter Description here"
                  name=""
                  id="desc"
                ></textarea>
              </div>
              <!-- Cover Image  -->
              <div class="col-12">
                <label for="coverImage" class="form-label label-design"
                  >Cover Image</label
                >
                <div class="relative coverImageWrapper">
                  <input
                    type="text"
                    disabled
                    class="form-control input-design"
                    id="coverImage"
                    placeholder="Upload cover image here"
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

              <div style="margin-top: 31px" class="col-12">
                <button
                  class="btn btn-primary btn-design"
                  @click="continueStep()"
                >
                  Continue
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
    continueStep() {
      this.showDrawer = false;
      this.$emit("continueStep");
    },
  },
};
</script>

<style lang="scss" scoped>
.text-right {
  //   position: fixed;
  //   background-color: #fff;
  width: 100%;
  display: flex;
  justify-content: flex-end;
  img {
    // padding-right: 20px;
    // padding-top: 20px;
  }
}
</style>
