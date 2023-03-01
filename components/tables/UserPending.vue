<template>
  <div>
    <v-data-table
      :headers="headers"
      :mobile-breakpoint="766"
      :disable-filtering="true"
      :disable-sort="true"
      :items="admin"
      :items-per-page="5"
      class="generic__table"
    >
      <!-- user details  -->
      <template v-slot:item.user="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <div class="images__container">
              <img src="/images/temporary/profile.jpg" alt="avatar" />
            </div>
            <div>
              <span>
                <nuxt-link to="/users/3444">{{ item.user }}</nuxt-link></span
              >
              <p class="username">{{ item.userName }}</p>
            </div>
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

      <!-- number  -->
      <template v-slot:item.number="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p>
              <a :href="`tel:${item.number}`">{{ item.number }}</a>
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

      <!-- plan  -->
      <template v-slot:item.plan="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <div class="chip__wrapper">
              <div v-for="(item, index) in item.plans" :key="index">
                <v-chip
                  small
                  text-color="var(--primary-color)"
                  color="var(--input-bg)"
                  :ripple="false"
                  class="plan__chips"
                >
                  {{ item }}
                </v-chip>
              </div>
            </div>
          </div>
        </div>
      </template>

      <!-- status  -->
      <template v-slot:item.status="{ item }">
        <div class="user_content">
          <div class="user_content_details">
            <p
              :class="{
                verified: item.status == 'verified',
                pending: item.status == 'pending',
              }"
            >
              {{ item.status }}
            </p>
          </div>
        </div>
      </template>

      <!-- action  -->
      <template v-slot:item.action="{ item }">
        <div class="user_content_details" style="justify-content: center">
          <v-menu offset-y min-width="156">
            <template v-slot:activator="{ on, attrs }">
              <div v-bind="attrs" v-on="on" class="action__activator user">
                <svg
                  width="17"
                  height="4"
                  viewBox="0 0 17 4"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <g clip-path="url(#clip0_458_67292)">
                    <path
                      d="M6.89022 1.83858C6.89022 2.85374 7.71316 3.67668 8.72831 3.67668C9.74346 3.67668 10.5664 2.85374 10.5664 1.83858C10.5664 0.823431 9.74346 0.000488245 8.72831 0.000488201C7.71316 0.000488157 6.89022 0.823431 6.89022 1.83858Z"
                      fill="#333940"
                    />
                    <path
                      d="M13.3238 1.83858C13.3238 2.85374 14.1468 3.67668 15.1619 3.67668C16.1771 3.67668 17 2.85374 17 1.83858C17 0.823431 16.1771 0.000488245 15.1619 0.000488201C14.1468 0.000488157 13.3238 0.823431 13.3238 1.83858Z"
                      fill="#333940"
                    />
                    <path
                      d="M0.45711 1.83858C0.45711 2.85374 1.28005 3.67668 2.29521 3.67668C3.31036 3.67668 4.1333 2.85374 4.1333 1.83858C4.1333 0.823431 3.31036 0.000488245 2.29521 0.000488201C1.28005 0.000488157 0.45711 0.823431 0.45711 1.83858Z"
                      fill="#333940"
                    />
                  </g>
                  <defs>
                    <clipPath id="clip0_458_67292">
                      <rect
                        width="3.67619"
                        height="16.5429"
                        fill="white"
                        transform="translate(17) rotate(90)"
                      />
                    </clipPath>
                  </defs>
                </svg>
              </div>
            </template>
            <v-list class="dropdown__list">
              <nuxt-link to="/users/3444?verify=1">
                <v-list-item class="dropdown__list-item">
                  <v-list-item-title class="dropdown__list-title"
                    >Verify User</v-list-item-title
                  >
                </v-list-item>
              </nuxt-link>
              <v-list-item
                @click="showPanel('edit')"
                class="dropdown__list-item"
              >
                <v-list-item-title class="dropdown__list-title"
                  >Edit User</v-list-item-title
                >
              </v-list-item>
            </v-list>
          </v-menu>
        </div>
      </template>
    </v-data-table>
    <ViewAdmin @showEdit="showPanel('edit')" ref="adminView" />
    <EditUser ref="userEdit" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      headers: [
        {
          text: "USER NAME",
          align: "start",
          sortable: false,
          value: "user",
        },
        { text: "Email", value: "email" },
        { text: "PHONE NUMBER", value: "number" },
        { text: "BALANCE", value: "balance" },
        { text: "PLANS", value: "plan" },
        { text: "STAUS", value: "status" },
        { text: "ACTION", value: "action" },
      ],
      admin: [
        {
          user: "Bellingham Jude",
          userName: "@bellingjude",
          email: "bellighamj@gmail.com",
          number: "09087676578",
          balance: "₦100,000",
          plans: ["savings", "investibox", "loan", "jollification"],
          status: "pending",
        },
        {
          user: "John Doe",
          userName: "@johndoe",
          email: "bellighamj@gmail.com",
          number: "09087676578",
          balance: "₦100,000",
          plans: ["savings", "investibox", "jollification"],
          status: "pending",
        },
        {
          user: "John Kennedy",
          userName: "@johnkennedy",
          email: "johndoe@yahoo.com",
          number: "09087676578",
          balance: "₦100,000",
          plans: ["savings", "jollification"],
          status: "pending",
        },
        {
          user: "John Doe",
          userName: "@johndoe",
          email: "johndoe@yahoo.com",
          number: "09087676578",
          balance: "₦100,000",
          plans: ["savings"],
          status: "pending",
        },
        {
          user: "Collins Jude",
          userName: "@Collinsjude",
          email: "bellighamj@gmail.com",
          number: "09087676578",
          balance: "₦100,000",
          plans: ["savings", "investibox", "loan", "jollification"],
          status: "pending",
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