<template>
  <div>
    <v-data-table
      v-model="selected"
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
            <p class="approved">
              {{ item.user }}
            </p>
          </div>
        </div>
      </template>

      <!-- email  -->
      <template v-slot:item.email="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              <a :href="`mailto:${item.email}`">{{ item.email }}</a>
            </p>
          </div>
        </div>
      </template>

      <!-- phone  -->
      <template v-slot:item.phone="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              <a :href="`tel:${item.phone}`">{{ item.phone }}</a>
            </p>
          </div>
        </div>
      </template>

      <!-- due  -->
      <template v-slot:item.due="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>{{ item.due }}</p>
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
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: [],
      headers: [
        {
          text: "REFERRALS",
          align: "start",
          sortable: false,
          value: "user",
        },
        { text: "EMAILS", value: "email" },
        { text: "PHONE NUMBER", value: "phone" },
        { text: "STATUS", value: "due" },
        { text: "joined", value: "status" },
      ],
      admin: [
        {
          id: 1,
          user: "Ogechukwu Moe",
          email: "ogechukwumoe@gmail.com",
          phone: "09098672785",
          balance: 20,
          payment: "10%",
          due: "Active",
          category: "₦10,000",
          status: "22, Sept. 2022",
          open: "22, Sept. 2022",
          close: "22, Sept. 2022",
        },
        {
          id: 2,
          user: "Ogechukwu Moe",
          email: "ogechukwumoe@gmail.com",
          phone: "09098672785",
          balance: 20,
          payment: "10%",
          due: "Active",
          category: "₦10,000",
          status: "22, Sept. 2022",
          open: "22, Sept. 2022",
          close: "22, Sept. 2022",
        },
        {
          id: 3,
          user: "Ogechukwu Moe",
          email: "ogechukwumoe@gmail.com",
          phone: "09098672785",
          balance: 20,
          payment: "10%",
          due: "Active",
          category: "₦10,000",
          status: "22, Sept. 2022",
          open: "22, Sept. 2022",
          close: "22, Sept. 2022",
        },
        {
          id: 4,
          user: "John Doe",
          email: "ogechukwumoe@gmail.com",
          phone: "09098672785",
          balance: 20,
          payment: "10%",
          due: "Active",
          category: "₦10,000",
          status: "22, Sept. 2022",
          open: "22, Sept. 2022",
          close: "22, Sept. 2022",
        },
        {
          id: 5,
          user: "Kenneth Cole",
          email: "ogechukwumoe@gmail.com",
          phone: "09098672785",
          balance: 20,
          payment: "10%",
          due: "Active",
          category: "₦10,000",
          status: "22, Sept. 2022",
          open: "22, Sept. 2022",
          close: "22, Sept. 2022",
        },
        {
          id: 6,
          user: "Kenneth Cole",
          email: "ogechukwumoe@gmail.com",
          phone: "09098672785",
          balance: 20,
          payment: "10%",
          due: "Active",
          category: "₦10,000",
          status: "22, Sept. 2022",
          open: "22, Sept. 2022",
          close: "22, Sept. 2022",
        },
      ],
    };
  },
  methods: {
    showPanel(type) {
      switch (type) {
        case "jollyPlan":
          this.$refs.jollyPlan.showPanel();
          break;
        case "disableLoan":
          this.$refs.disableLoan.showPanel();
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