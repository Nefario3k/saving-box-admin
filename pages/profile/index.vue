<template>
  <div>
    <v-row class="row__content">
      <div class="col-12">
        <v-card color="#fff" class="profile__card">
          <header>Manage Profile</header>
          <!-- tab control  -->
          <v-tabs
            :show-arrows="false"
            v-model="profileTab"
            background-color="transparent"
            color="var(--primary-color)"
            class="profile__card-tabs"
          >
            <v-tabs-slider color="var(--primary-color)"></v-tabs-slider>
            <v-tab class="profile__card-tab"> Account </v-tab>
            <v-tab class="profile__card-tab"> Security </v-tab>
          </v-tabs>
          <v-divider class="profile__card-divider"></v-divider>

          <!-- tab items  -->
          <v-tabs-items v-model="profileTab" class="profile__card-tabItems">
            <v-tab-item>
              <ProfileSettings />
            </v-tab-item>

            <v-tab-item>
              <!-- empty state -->
              <ProfileSecurity />
            </v-tab-item>
          </v-tabs-items>
        </v-card>
      </div>
    </v-row>
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
  // page properties go here
};
</script>

<style scoped>
/* page style */
.my-savings-stats {
  margin-top: 40px;
  margin-bottom: 44px;
}

.my-savings-stats-item {
  padding: 24px;
  border-radius: 10px;
  background-color: rgba(255, 231, 175, 1);
}

.my-savings-stats-item p {
  font-weight: 400;
  font-size: 16px;
  /* line-height: 35.13px; */
  color: rgba(0, 8, 49, 1);
  margin-bottom: 0px;
}

.my-savings-stats-item h1 {
  font-weight: 600;
  font-size: 25px;
  /* line-height: 35.13px; */
  color: rgba(0, 8, 49, 1);
}

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

/* create-savings-btn */
.create-savings-btn {
  padding: 16px 24px 16px 24px;
  color: white !important;
  font-weight: 600;
  font-size: 18px;
  text-decoration: none;
}

.create-savings-btn img {
  margin-right: 15px;
  color: white;
}
</style>
