<template>
  <div>
    <v-data-table
      :headers="headers"
      :mobile-breakpoint="766"
      :disable-filtering="true"
      :disable-sort="true"
      :items="admin"
      :single-select="false"
      show-select
      item-key="id"
      :items-per-page="5"
      class="generic__table selectTable noAction"
    >
      <!-- user details  -->
      <template v-slot:item.user="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <div>
              <span @click="showPanel('view')">{{ item.user }}</span>
            </div>
          </div>
        </div>
      </template>

      <!-- email  -->
      <template v-slot:item.email="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              {{ item.email }}
            </p>
          </div>
        </div>
      </template>

      <!-- number  -->
      <template v-slot:item.number="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              {{ item.number }}
            </p>
          </div>
        </div>
      </template>

      <!-- balance  -->
      <template v-slot:item.balance="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>{{ item.balance }}</p>
          </div>
        </div>
      </template>

      <!-- status  -->
      <template v-slot:item.status="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              {{ item.status }}
            </p>
          </div>
        </div>
      </template>

      <!-- statusTwo  -->
      <template v-slot:item.statusTwo="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              {{ item.statusTwo }}
            </p>
          </div>
        </div>
      </template>
    </v-data-table>
    <ViewUserPlans @showEdit="showPanel('edit')" ref="adminView" />
    <EditUser ref="userEdit" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: [],
      headers: [
        {
          text: "TRANSACTION",
          align: "start",
          sortable: false,
          value: "user",
        },
        { text: "PLAN TYPE", value: "email" },
        { text: "AMOUNT", value: "balance" },
        { text: "PERIOD", value: "number" },
        { text: "DUE DATE", value: "status" },
        { text: "CREATED AT", value: "statusTwo" },
      ],
      admin: [
        {
          id: 1,
          user: "Children’s Fee Plan",
          email: "Autobox",
          number: "6 Months",
          balance: "₦100,000",
          plans: 40,
          status: "22, Sept. 2022",
          statusTwo: "22, Sept. 2022",
        },
        {
          id: 2,
          user: "Children’s Fee Plan",
          email: "Safelock Box",
          number: "6 Months",
          balance: "₦100,000",
          plans: 60,
          status: "22, Sept. 2022",
          statusTwo: "22, Sept. 2022",
        },
        {
          id: 3,
          user: "Housing and Rent",
          email: "Autobox",
          number: "6 Months",
          balance: "₦100,000",
          plans: 30,
          status: "22, Sept. 2022",
          statusTwo: "22, Sept. 2022",
        },
        {
          id: 4,
          user: "Housing and Rent",
          email: "Target Box",
          number: "6 Months",
          balance: "₦100,000",
          plans: 40,
          status: "22, Sept. 2022",
          statusTwo: "22, Sept. 2022",
        },
        {
          id: 5,
          user: "Housing and Rent",
          email: "Simple Box",
          number: "6 Months",
          balance: "₦100,000",
          plans: 85,
          status: "22, Sept. 2022",
          statusTwo: "22, Sept. 2022",
        },
      ],
    };
  },
  methods: {
    showPanel(type) {
      switch (type) {
        case "view":
          this.$refs.adminView.showPanel();
          break;
        case "edit":
          this.$refs.userEdit.showPanel();
          break;

        default:
          break;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.chip__wrapper {
  display: flex;
  align-items: center;
  gap: 4px;
  flex-wrap: wrap;
}
</style>