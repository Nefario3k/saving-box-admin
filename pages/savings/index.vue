<template>
  <div>
    <v-row class="row__content">
      <div class="col-12">
        <v-card color="#fff" class="profile__card not__profile__card">
          <header>
            <span>Savings <span class="value">(4)</span></span>
          </header>
          <v-divider style="margin: 0 -33px 10px 0"></v-divider>

          <div class="row m-0 mb-5">
            <!-- cards   -->
            <div
              class="col-6 col-lg-3 col-xl-3 card__container savings"
              v-for="(items, index) in cardDetails"
              :key="index"
            >
              <DashboardCard :card="items" />
            </div>
          </div>

          <SearchArea placeholder="Search by Plan Name, and duration" />
          <TablesSavingPage />
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
      cardDetails: [
        {
          title: "Total Autobox Savings",
          value: "₦240,000,000",
          details: "",
          color: "var(--card-eight)",
        },
        {
          title: "Ongoing Savings",
          value: "24",
          details: "",
          color: "var(--card-nine)",
        },
        {
          title: "Completed Savings",
          value: "19",
          details: "",
          color: "var(--card-ten)",
        },
        {
          title: "Liquidated Savings",
          value: "09",
          details: "",
          color: "var(--card-alt-one)",
        },
      ],
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
