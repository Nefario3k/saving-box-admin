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
              <span>{{ item.user }}</span>
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

      <!-- date  -->
      <template v-slot:item.date="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              {{ item.date }}
            </p>
          </div>
        </div>
      </template>

      <!-- balance  -->
      <template v-slot:item.balance="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p v-if="item.balance">{{ item.balance }}</p>
            <p v-else>Null</p>
          </div>
        </div>
      </template>

      <!-- plan  -->
      <template v-slot:item.plan="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p @click="showPanel('userDocs')" class="view">Preview</p>
          </div>
        </div>
      </template>

      <!-- status  -->
      <template v-slot:item.status="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p
              :class="{
                verified: item.status == 'approved',
                danger: item.status == 'unapproved',
              }"
            >
              {{ item.status }}
            </p>
          </div>
        </div>
      </template>

      <!-- action  -->
      <template v-slot:item.action="{ item }">
        <div class="user_content_details">
          <v-btn color="#666B70" outlined class="downloadBtn">
            <svg
              width="20"
              height="21"
              viewBox="0 0 20 21"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                clip-rule="evenodd"
                d="M6.13916 6.94375C6.48416 6.94375 6.76416 7.22375 6.76416 7.56875C6.76416 7.91375 6.48416 8.19375 6.13916 8.19375H5.35499C4.00999 8.19375 2.91666 9.28625 2.91666 10.6304V14.7013C2.91666 16.0504 4.01332 17.1471 5.36249 17.1471H14.6458C15.9892 17.1471 17.0833 16.0529 17.0833 14.7096V10.6396C17.0833 9.29042 15.9858 8.19375 14.6383 8.19375H13.8617C13.5167 8.19375 13.2367 7.91375 13.2367 7.56875C13.2367 7.22375 13.5167 6.94375 13.8617 6.94375H14.6383C16.6758 6.94375 18.3333 8.60208 18.3333 10.6396V14.7096C18.3333 16.7429 16.6783 18.3971 14.6458 18.3971H5.36249C3.32499 18.3971 1.66666 16.7396 1.66666 14.7013V10.6304C1.66666 8.59708 3.32082 6.94375 5.35499 6.94375H6.13916ZM10.0007 3C10.3457 3 10.6257 3.28 10.6257 3.625L10.625 12.1467L11.9882 10.7783C12.2315 10.5333 12.6265 10.5333 12.8715 10.7767C13.1157 11.02 13.1165 11.4158 12.8732 11.6608L10.4488 14.0947C10.4251 14.1191 10.3995 14.1415 10.3721 14.1617L10.4432 14.1C10.4163 14.1272 10.3872 14.1517 10.3562 14.1732C10.3373 14.1862 10.3181 14.198 10.2983 14.2088C10.2887 14.214 10.2787 14.2191 10.2685 14.224C10.2503 14.2326 10.2317 14.2404 10.2126 14.2473C10.203 14.2507 10.1934 14.2538 10.1838 14.2568C10.1603 14.2641 10.1362 14.2699 10.1116 14.2743C10.106 14.2753 10.101 14.2761 10.0959 14.2769C10.076 14.28 10.0553 14.2822 10.0343 14.2833C10.0229 14.2839 10.0118 14.2842 10.0007 14.2842L9.96749 14.2817L9.91588 14.2785C9.91221 14.278 9.90854 14.2774 9.90488 14.2769L10.0007 14.2842C9.96342 14.2842 9.92647 14.2808 9.89024 14.2744C9.86518 14.2699 9.8411 14.2641 9.8176 14.2569C9.80822 14.2539 9.799 14.2509 9.78986 14.2476C9.77071 14.2408 9.75179 14.233 9.73338 14.2242C9.72219 14.2189 9.71107 14.2133 9.70011 14.2072C9.68472 14.1987 9.66988 14.1897 9.65546 14.1802C9.64558 14.1737 9.6357 14.1667 9.62602 14.1594C9.60221 14.1415 9.57976 14.122 9.55878 14.101L9.55816 14.1L7.12816 11.6608C6.88482 11.4158 6.88566 11.02 7.12982 10.7767C7.37482 10.5333 7.76982 10.5333 8.01316 10.7783L9.37499 12.1467L9.37566 3.625C9.37566 3.28 9.65566 3 10.0007 3Z"
                fill="#666B70"
              />
            </svg>

            <span>Download</span>
          </v-btn>
        </div>
      </template>
    </v-data-table>
    <ViewUserDocs :pdfUrl="pdfUrl" ref="userDocs" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      selected: [],
      headers: [
        {
          text: "VERIFICATION",
          align: "start",
          sortable: false,
          value: "user",
        },
        { text: "File", value: "email" },
        { text: "NUMBER", value: "balance" },
        { text: "STATUS", value: "status" },
        { text: "View", value: "plan" },
        { text: "DOWNLOAD", value: "action" },
      ],
      admin: [
        {
          id: 1,
          user: "Government Identification",
          email: "National ID.pdf",
          number: "6 Months",
          balance: "22348599599",
          status: "approved",
          date: "22, Sept. 2022",
        },
        {
          id: 2,
          user: "Proof of Address",
          email: "AEDC Bill ID.pdf",
          number: "6 Months",
          balance: null,
          status: "unapproved",
          date: "22, Sept. 2022",
        },
      ],
      pdfUrl: "/sample.pdf",
    };
  },
  methods: {
    showPanel(type) {
      switch (type) {
        case "userDocs":
          this.$refs.userDocs.showPanel();
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