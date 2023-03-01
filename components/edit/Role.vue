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
            <h1 class="">Edit Roles</h1>
          </div>

          <section class="input__area update-form">
            <div class="row">
              <!-- name  -->
              <div class="col-12">
                <label for="roleName" class="form-label label-design"
                  >Role Name</label
                >
                <input
                  type="text"
                  disabled
                  class="form-control input-design"
                  id="roleName"
                  value="Compliant Officer"
                  placeholder="Role Name"
                />
              </div>
              <!-- description  -->
              <div class="col-12">
                <label for="description" class="form-label label-design"
                  >Description</label
                >
                <input
                  type="text"
                  class="form-control input-design"
                  id="description"
                  placeholder="Description"
                />
              </div>

              <div class="col-12 permissions">
                <span>Assign Permission</span>

                <v-expansion-panels multiple flat class="selectPanels">
                  <!-- user activities  -->
                  <v-expansion-panel class="selectPanels__panel">
                    <v-expansion-panel-header
                      class="selectPanels__panel-header"
                    >
                      User Activities
                    </v-expansion-panel-header>
                    <v-expansion-panel-content
                      class="selectPanels__panel-content"
                    >
                      <div class="content__wrapper">
                        <v-checkbox
                          label="Can edit user"
                          color="var(--primary-color)"
                          hide-details
                          value="true"
                        ></v-checkbox>
                        <v-checkbox
                          label="Can view user"
                          color="var(--primary-color)"
                          hide-details
                          value="true"
                        ></v-checkbox>
                        <v-checkbox
                          label="Can suspend user"
                          color="var(--primary-color)"
                          hide-details
                          value="true"
                        ></v-checkbox>
                        <v-checkbox
                          label="Can delete user"
                          color="var(--primary-color)"
                          hide-details
                          :value="true"
                        ></v-checkbox>
                      </div>
                    </v-expansion-panel-content>
                  </v-expansion-panel>

                  <!-- Loan Activities  -->
                  <v-expansion-panel class="selectPanels__panel">
                    <v-expansion-panel-header
                      class="selectPanels__panel-header"
                    >
                      Loan Activities
                    </v-expansion-panel-header>
                    <v-expansion-panel-content
                      class="selectPanels__panel-content"
                    >
                      <div class="content__wrapper">
                        <v-checkbox
                          label="Can edit user"
                          color="var(--primary-color)"
                          hide-details
                          value="true"
                        ></v-checkbox>
                        <v-checkbox
                          label="Can view user"
                          color="var(--primary-color)"
                          hide-details
                          value="true"
                        ></v-checkbox>
                      </div>
                    </v-expansion-panel-content>
                  </v-expansion-panel>

                  <!-- Savings Activities  -->
                  <v-expansion-panel class="selectPanels__panel">
                    <v-expansion-panel-header
                      class="selectPanels__panel-header"
                    >
                      Savings Activities
                    </v-expansion-panel-header>
                    <v-expansion-panel-content
                      class="selectPanels__panel-content"
                    >
                      <div class="content__wrapper">
                        <v-checkbox
                          label="Can edit user"
                          color="var(--primary-color)"
                          hide-details
                          value="true"
                        ></v-checkbox>
                        <v-checkbox
                          label="Can view user"
                          color="var(--primary-color)"
                          hide-details
                          value="true"
                        ></v-checkbox>
                      </div>
                    </v-expansion-panel-content>
                  </v-expansion-panel>
                </v-expansion-panels>
              </div>

              <div style="margin-top: 57px" class="col-12">
                <button class="btn btn-primary btn-design">Update</button>
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
