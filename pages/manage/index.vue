<template>
  <div>
    <v-row class="row__content">
      <div class="col-12">
        <v-card color="#fff" class="profile__card not__profile__card">
          <!-- tab control  -->
          <v-tabs
            :show-arrows="true"
            v-model="profileTab"
            background-color="transparent"
            color="var(--primary-color)"
            class="profile__card-tabs"
          >
            <v-tabs-slider color="var(--primary-color)"></v-tabs-slider>
            <v-tab class="profile__card-tab not__profile__card-tabs">
              Administrators
            </v-tab>
            <v-tab class="profile__card-tab not__profile__card-tabs">
              Roles
            </v-tab>
            <v-tab class="profile__card-tab not__profile__card-tabs">
              Activity Log
            </v-tab>
          </v-tabs>
          <v-divider class="profile__card-divider"></v-divider>

          <!-- tab items  -->
          <v-tabs-items v-model="profileTab" class="profile__card-tabItems">
            <v-tab-item>
              <header>
                <span>Manage Admin</span>
                <v-btn
                  @click="showPanel('createAdmin')"
                  class="Btn"
                  color="var(--primary-color)"
                  ><span>Create New Admin</span></v-btn
                >
              </header>
              <TablesAdmin />
            </v-tab-item>

            <v-tab-item>
              <header>
                <span>Manage Roles</span>
                <v-btn
                  @click="showPanel('createRole')"
                  class="Btn"
                  color="var(--primary-color)"
                  ><span>Create New Role</span></v-btn
                >
              </header>
              <TablesRole />
            </v-tab-item>

            <v-tab-item>
              <header><span>Manage Activities</span></header>
              <TablesActivity />
            </v-tab-item>
          </v-tabs-items>
        </v-card>
      </div>
    </v-row>
    <CreateAdmin @createAdmin="createAdmin" ref="createAdmin" />
    <CreateRole ref="createRole" />
    <StatusTile
      :absolute="false"
      :fixed="true"
      :border="false"
      :top="77"
      :right="statusRight"
      color="var(--green)"
      header="Admin Created!"
      headerColor="#fff"
      subtext="Admin created successfully"
      subtextColor="#fff"
      :svg="true"
      svgStroke="var(--green)"
      svgColor="#fff"
      :index="33"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      profileTab: null,
      paymentTab: null,
      statusRight: -500,
    };
  },
  methods: {
    showPanel(type) {
      switch (type) {
        case "createAdmin":
          this.$refs.createAdmin.showPanel();
          break;
        case "createRole":
          this.$refs.createRole.showPanel();
          break;

        default:
          break;
      }
    },
    createAdmin() {
      this.statusRight = 31;
      setTimeout(() => {
        this.statusRight = -500;
      }, 2000);
    },
  },
  // page properties go here
};
</script>

<style scoped>
/* tab */
.v-tabs-bar .v-tab:not(.v-tab--active) {
  color: rgba(102, 107, 112, 1) !important;
  font-weight: 600 !important;
  font-size: 14px !important;
  text-transform: capitalize;
}

.v-tab--active {
  background-color: #ffffff;
  border-radius: 4px;
  font-weight: 600;
  font-size: 14px;
  color: rgba(65, 105, 225, 1) !important;
  text-transform: capitalize;
}
</style>
