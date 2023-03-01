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
      :permanent="false"
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
            <h1 class="">Edit Jollification Plan</h1>
            <p>Create Items and Amount</p>
          </div>

          <section class="input__area update-form">
            <div class="row">
              <!-- controller  -->
              <div class="col-12">
                <div v-for="n in 5" :key="n" class="jollyItems">
                  <div class="leftSide">
                    <img src="/images/temporary/generator.png" alt="" />
                    <div>
                      <p>Generator</p>
                      <span>Description</span>
                    </div>
                  </div>
                  <div class="rightSide">
                    <p>₦10,000</p>
                    <v-menu offset-y min-width="127">
                      <template v-slot:activator="{ on, attrs }">
                        <svg
                          v-bind="attrs"
                          v-on="on"
                          width="5"
                          height="18"
                          viewBox="0 0 5 18"
                          fill="none"
                          xmlns="http://www.w3.org/2000/svg"
                        >
                          <g clip-path="url(#clip0_1493_90040)">
                            <path
                              d="M2.72831 6.99959C1.71316 6.99959 0.890216 7.82253 0.890216 8.83769C0.890216 9.85284 1.71316 10.6758 2.72831 10.6758C3.74346 10.6758 4.56641 9.85284 4.56641 8.83769C4.56641 7.82253 3.74346 6.99959 2.72831 6.99959Z"
                              fill="#4169E1"
                            />
                            <path
                              d="M2.72831 13.4332C1.71316 13.4332 0.890216 14.2561 0.890216 15.2713C0.890216 16.2864 1.71316 17.1094 2.72831 17.1094C3.74346 17.1094 4.56641 16.2864 4.56641 15.2713C4.56641 14.2561 3.74346 13.4332 2.72831 13.4332Z"
                              fill="#4169E1"
                            />
                            <path
                              d="M2.72831 0.565997C1.71316 0.565997 0.890216 1.38894 0.890216 2.40409C0.890216 3.41924 1.71316 4.24219 2.72831 4.24219C3.74346 4.24219 4.56641 3.41924 4.56641 2.40409C4.56641 1.38894 3.74346 0.565997 2.72831 0.565997Z"
                              fill="#4169E1"
                            />
                          </g>
                          <defs>
                            <clipPath id="clip0_1493_90040">
                              <rect
                                width="3.67619"
                                height="16.5429"
                                fill="white"
                                transform="translate(4.56689 17.1094) rotate(-180)"
                              />
                            </clipPath>
                          </defs>
                        </svg>
                      </template>
                      <v-list class="dropdown__list">
                        <v-list-item class="dropdown__list-item">
                          <v-list-item-title class="dropdown__list-title"
                            >Edit</v-list-item-title
                          >
                        </v-list-item>
                        <v-list-item class="dropdown__list-item delete">
                          <v-list-item-title class="dropdown__list-title"
                            >Delete</v-list-item-title
                          >
                        </v-list-item>
                      </v-list>
                    </v-menu>
                  </div>
                </div>
              </div>
              <div class="col-12 addJolly">
                <v-btn
                  @click="showAddJolly"
                  outlined
                  color="var(--primary-color)"
                  class="Btn"
                  >Add New Item</v-btn
                >
              </div>

              <div style="margin-top: 31px" class="col-12">
                <button
                  @click="showSuccess = !showSuccess"
                  class="btn btn-primary btn-design"
                >
                  Finish Updating
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

            <h1 class="">Updated Successfully</h1>
            <p
              style="
                margin: 0 auto !important;
                width: 85%;
                font-size: 1.8rem;
                color: var(--label-color);
              "
            >
              Your Jollification plan has been updated successfully.
            </p>
          </div>
          <section class="input__area update-form">
            <div class="row">
              <div style="margin-top: 76px" class="pt-0 col-12">
                <button class="btn btn-primary btn-design">
                  Back to Dashboard
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
    showAddJolly() {
      this.showDrawer = false;
      this.$emit("showAddJolly");
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
</style>
