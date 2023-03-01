<template>
  <div>
    <v-row class="row__content">
      <div class="col-12">
        <v-card color="#fff" class="profile__card not__profile__card">
          <header>
            <span>Users <span class="value">(1,508)</span></span>
            <v-btn class="Btn Btn--light" color="var(--primary-light-color)"
              ><span>Add New User</span></v-btn
            >
          </header>
          <v-divider style="margin: 0 -33px 10px 0"></v-divider>
          <!-- tab control  -->
          <v-tabs
            v-model="profileTab"
            background-color="transparent"
            color="var(--primary-color)"
            class="profile__card-tabs"
          >
            <v-tabs-slider color="var(--primary-color)"></v-tabs-slider>
            <v-tab class="profile__card-tab not__profile__card-tabs">
              All Users
            </v-tab>
            <v-tab class="profile__card-tab not__profile__card-tabs">
              Pending Verification
            </v-tab>
          </v-tabs>
          <v-divider
            style="margin-bottom: 18px"
            class="profile__card-divider"
          ></v-divider>

          <SearchUser placeholder="Search by Name, Email & Phone Number" />

          <!-- tab items  -->
          <v-tabs-items v-model="profileTab" class="profile__card-tabItems">
            <v-tab-item>
              <TablesUser />
            </v-tab-item>

            <v-tab-item>
              <TablesUserPending />
            </v-tab-item>
          </v-tabs-items>
        </v-card>
      </div>
    </v-row>
    <CreateAdmin ref="createAdmin" />
    <CreateRole ref="createRole" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      profileTab: null,
      paymentTab: null,
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
