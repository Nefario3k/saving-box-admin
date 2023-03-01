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
            <p class="approved">
              {{ item.email }}
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
          text: "NAME",
          align: "start",
          sortable: false,
          value: "user",
        },
        { text: "ACTION DONE", value: "email" },
        { text: "TARGET AMOUNT", value: "balance" },
        { text: "CREATED AT", value: "status" },
      ],
      admin: [
        {
          id: 1,
          user: "Uchiha Madara",
          email: 100,
          balance: "₦100,000",
          status: "22, Sept. 2022",
        },
        {
          id: 2,
          user: "Maxwell Jogn",
          email: 2,
          balance: "₦100,000",
          status: "22, Sept. 2022",
        },
        {
          id: 3,
          user: "Victor Damian",
          email: 4,
          balance: "₦100,000",
          status: "22, Sept. 2022",
        },
        {
          id: 4,
          user: "Kenneth Cole",
          email: 5,
          balance: "₦100,000",
          status: "22, Sept. 2022",
        },
        {
          id: 5,
          user: "John Doe",
          email: 6,
          balance: "₦100,000",
          status: "22, Sept. 2022",
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