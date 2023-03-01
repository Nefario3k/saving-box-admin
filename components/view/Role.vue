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
            <h1 class="">Permissions</h1>
          </div>

          <section class="input__area update-form">
            <div class="row">
              <!-- name  -->
              <div class="col-12">
                <label class="form-label label-design">Role</label>
                <v-menu :nudge-bottom="3" offset-y max-height="190">
                  <template v-slot:activator="{ on, attrs }">
                    <div v-bind="attrs" v-on="on" class="relative">
                      <input
                        style="cursor: pointer"
                        type="text"
                        disabled
                        value="Compliant Officer"
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
                        >Compliant Officer</v-list-item-title
                      >
                    </v-list-item>
                  </v-list>
                </v-menu>
              </div>

              <div class="col-12 permissions">
                <span>Users</span>

                <div class="content__wrapper-view">
                  <v-checkbox
                    v-model="checkedData"
                    label="Can edit user"
                    color="var(--primary-color)"
                    hide-details
                    disabled
                    checked
                  ></v-checkbox>
                  <v-checkbox
                    v-model="checkedData"
                    label="Can view user"
                    color="var(--primary-color)"
                    hide-details
                    disabled
                    checked
                  ></v-checkbox>
                  <v-checkbox
                    v-model="checkedData"
                    label="Can suspend user"
                    color="var(--primary-color)"
                    hide-details
                    disabled
                    checked
                  ></v-checkbox>
                  <v-checkbox
                    v-model="checkedData"
                    label="Can delete user"
                    color="var(--primary-color)"
                    hide-details
                    disabled
                    checked
                  ></v-checkbox>
                  <v-checkbox
                    v-model="checkedData"
                    label="Can edit user"
                    color="var(--primary-color)"
                    hide-details
                    disabled
                    checked
                  ></v-checkbox>
                  <v-checkbox
                    v-model="checkedData"
                    label="Can view user"
                    color="var(--primary-color)"
                    hide-details
                    disabled
                    checked
                  ></v-checkbox>
                  <v-checkbox
                    v-model="checkedData"
                    label="Can suspend user"
                    color="var(--primary-color)"
                    hide-details
                    disabled
                    checked
                  ></v-checkbox>
                  <v-checkbox
                    v-model="checkedData"
                    label="Can delete user"
                    color="var(--primary-color)"
                    hide-details
                    disabled
                    checked
                  ></v-checkbox>
                </div>
              </div>

              <div
                style="min-height: 30vh; margin-top: 57px"
                class="relative col-12"
              >
                <button
                  @click="showEditPanel"
                  style="bottom: 0; left: 0"
                  class="absolute btn btn-primary btn-design"
                >
                  Edit
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
      checkedData: true,
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
    showEditPanel() {
      this.showDrawer = false;
      this.$emit("showEdit");
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
