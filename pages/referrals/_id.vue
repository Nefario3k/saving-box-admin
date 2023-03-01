<template>
  <div>
    <v-row class="row__content">
      <div class="col-12">
        <v-card color="#fff" class="profile__card not__profile__card">
          <header>
            <span><span class="value">Ogechukwu Moe</span></span>
          </header>
          <v-divider style="margin: 0 -33px 10px 0"></v-divider>
          <div class="titlePageTab">
            <p>Referrals</p>
          </div>

          <SearchArea placeholder="Search by Title Name, and Category" />
          <p class="amount">Total Commission <span>₦10,000</span></p>
          <TablesSingleReferral />
        </v-card>
      </div>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {
    showPanel(type) {
      switch (type) {
        case "createJolly":
          this.$refs.createJolly.showPanel();
          break;
        case "createJollyContinue":
          this.$refs.createJollyContinue.showPanel();
          break;
        case "createRole":
          this.$refs.createRole.showPanel();
          break;
        case "addJolly":
          this.$refs.addJolly.showPanel();
          break;

        default:
          break;
      }
    },
  },
  // page properties go here
};
</script>

<style scoped lang="scss">
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
.v-tabs-styles .v-tabs-bar .v-tab:not(.v-tab--active) {
  color: var(--label-second-color) !important;
  font-weight: 600 !important;
  font-size: 14px !important;
  text-transform: capitalize;
  margin: 3px 3px 2px 3px;
  transition: all 0.2s ease-in-out;
}
.v-tabs-styles .v-tabs-bar .v-tab {
  &::before {
    display: none;
  }
}

.v-tabs-styles .v-tab--active {
  transition: all 0.2s ease-in-out;
  background-color: #ffffff;
  margin: 3px 3px 2px 3px;
  border-radius: 4px;
  font-weight: 600;
  font-size: 14px;
  color: var(--primary-color) !important;
  text-transform: capitalize;
}
.amount {
  margin: 13px 0 13px;
  font-weight: 400;
  font-size: 1.6rem;
  color: var(--label-color);
  span {
    font-weight: 500;
    color: var(--label-third-color);
    padding-left: 7px;
  }
}
</style>
