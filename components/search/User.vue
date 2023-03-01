<template>
  <div class="searchArea">
    <div class="inputArea relative">
      <input
        type="text"
        :placeholder="placeholder"
        name=""
        value=""
        autocomplete="off"
      />
      <div class="searchIcon absolute">
        <svg
          width="20"
          height="20"
          viewBox="0 0 20 20"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <g clip-path="url(#clip0_498_73373)">
            <path
              d="M15.0262 13.8473L18.5953 17.4157L17.4162 18.5948L13.8478 15.0257C12.5201 16.09 10.8687 16.6689 9.16699 16.6665C5.02699 16.6665 1.66699 13.3065 1.66699 9.1665C1.66699 5.0265 5.02699 1.6665 9.16699 1.6665C13.307 1.6665 16.667 5.0265 16.667 9.1665C16.6694 10.8682 16.0905 12.5196 15.0262 13.8473ZM13.3545 13.229C14.4121 12.1414 15.0027 10.6835 15.0003 9.1665C15.0003 5.94317 12.3895 3.33317 9.16699 3.33317C5.94366 3.33317 3.33366 5.94317 3.33366 9.1665C3.33366 12.389 5.94366 14.9998 9.16699 14.9998C10.684 15.0022 12.1419 14.4116 13.2295 13.354L13.3545 13.229Z"
              fill="#999C9F"
            />
          </g>
          <defs>
            <clipPath id="clip0_498_73373">
              <rect width="20" height="20" fill="white" />
            </clipPath>
          </defs>
        </svg>
      </div>
      <v-dialog v-model="dialog" fullscreen>
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            v-bind="attrs"
            v-on="on"
            color="var(--label-color)"
            outlined
            style="width: max-content"
            class="Btn d-none noDesktopBtn"
          >
            <svg
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <g clip-path="url(#clip0_498_73383)">
                <path
                  d="M10 18H14V16H10V18ZM3 6V8H21V6H3ZM6 13H18V11H6V13Z"
                  fill="#666B70"
                />
              </g>
              <defs>
                <clipPath id="clip0_498_73383">
                  <rect width="24" height="24" fill="white" />
                </clipPath>
              </defs>
            </svg>
          </v-btn>
        </template>
        <v-card>
          <v-list class="dropdown__list">
            <!-- control -->
            <v-list-item
              style="padding-top: 12px"
              class="dropdown__list-item noHover"
            >
              <div class="filter__header">
                <span>Filter</span>
                <v-btn class="Btn" color="var(--primary-light-color)">
                  <span>Reset</span>
                </v-btn>
                <svg
                  @click="dialog = false"
                  width="30"
                  height="30"
                  viewBox="0 0 30 30"
                  fill="none"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path
                    d="M22.5 7.5L7.5 22.5"
                    stroke="#063A06"
                    stroke-width="1.5"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  />
                  <path
                    d="M7.5 7.5L22.5 22.5"
                    stroke="#063A06"
                    stroke-width="1.5"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                  />
                </svg>
              </div>
            </v-list-item>

            <!-- Plan Subscription -->
            <v-list-item class="dropdown__list-item tag">
              <v-list-item-title class="tag-title"
                >Plan Subscription</v-list-item-title
              >
            </v-list-item>

            <!-- select  -->
            <v-list-item class="dropdown__list-item noHover pb-2">
              <div class="statusFilter">
                <v-checkbox
                  label="Savings"
                  color="var(--primary-color)"
                  hide-details
                  value="true"
                ></v-checkbox>
                <v-checkbox
                  label="Jollification"
                  color="var(--primary-color)"
                  hide-details
                  value="true"
                ></v-checkbox>
                <v-checkbox
                  label="Investibox"
                  color="var(--primary-color)"
                  hide-details
                  value="true"
                ></v-checkbox>
                <v-checkbox
                  label="Loan"
                  color="var(--primary-color)"
                  hide-details
                  value="true"
                ></v-checkbox>
              </div>
            </v-list-item>

            <!-- Wallet Balance -->
            <v-list-item class="dropdown__list-item tag">
              <v-list-item-title class="tag-title"
                >Wallet Balance</v-list-item-title
              >
            </v-list-item>

            <!-- select  -->
            <v-list-item class="dropdown__list-item noHover pb-2">
              <div class="statusFilter">
                <v-radio-group v-model="balance">
                  <v-radio
                    color="var(--primary-color)"
                    label="₦0 - ₦100,000"
                    :value="0"
                  ></v-radio>
                  <v-radio
                    color="var(--primary-color)"
                    label="₦100,000 - ₦500,000"
                    :value="10"
                  ></v-radio>
                  <v-radio
                    color="var(--primary-color)"
                    label="₦500,000 and Above"
                    :value="100"
                  ></v-radio>
                  <v-radio
                    color="var(--primary-color)"
                    label="Custom"
                    value="custom"
                  ></v-radio>
                </v-radio-group>
                <div class="minMax dateInput" v-if="balance == 'custom'">
                  <input type="number" placeholder="Min(₦)" /><input
                    type="number"
                    placeholder="Max(₦)"
                  />
                </div>
              </div>
            </v-list-item>

            <!-- Plan Status -->
            <v-list-item
              :class="{ 'm-0': balance != 'custom' }"
              class="dropdown__list-item tag"
            >
              <v-list-item-title class="tag-title"
                >Plan Status</v-list-item-title
              >
            </v-list-item>

            <!-- select  -->
            <v-list-item class="dropdown__list-item noHover pb-2">
              <div class="statusFilter">
                <v-radio-group v-model="status">
                  <v-radio
                    color="var(--primary-color)"
                    label="Active"
                    :value="0"
                  ></v-radio>
                  <v-radio
                    color="var(--primary-color)"
                    label="Inactive"
                    :value="10"
                  ></v-radio>
                </v-radio-group>
              </div>
            </v-list-item>

            <!-- tag -->
            <v-list-item class="m-0 dropdown__list-item tag">
              <v-list-item-title class="tag-title">Date</v-list-item-title>
            </v-list-item>

            <!-- select  -->
            <v-list-item class="dropdown__list-item noHover pb-2">
              <div class="statusFilter dates">
                <div class="dateInput">
                  <span class="label">From</span>
                  <input type="date" name="" value="" />
                </div>
                <div class="dateInput">
                  <span class="label">To</span>
                  <input type="date" name="" value="" />
                </div>

                <v-btn color="var(--primary-color)" class="Btn"
                  >Apply Filters</v-btn
                >
              </div>
            </v-list-item>
          </v-list>
        </v-card>
      </v-dialog>
    </div>
    <div class="search__actions">
      <v-menu
        max-height="90vh"
        :close-on-content-click="closeOnContent"
        min-width="360"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-btn
            v-bind="attrs"
            v-on="on"
            color="var(--label-color)"
            outlined
            class="Btn filter"
          >
            <svg
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <g clip-path="url(#clip0_498_73383)">
                <path
                  d="M10 18H14V16H10V18ZM3 6V8H21V6H3ZM6 13H18V11H6V13Z"
                  fill="#666B70"
                />
              </g>
              <defs>
                <clipPath id="clip0_498_73383">
                  <rect width="24" height="24" fill="white" />
                </clipPath>
              </defs>
            </svg>

            <span>Filter</span>
            <svg
              width="20"
              height="20"
              viewBox="0 0 20 20"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path d="M10 13.055L5 8.47168H15L10 13.055Z" fill="#666B70" />
            </svg>
          </v-btn>
        </template>
        <v-list class="dropdown__list">
          <!-- control -->
          <v-list-item
            style="padding-top: 12px"
            class="dropdown__list-item noHover"
          >
            <div class="filter__header">
              <span>Filter</span>
              <v-btn class="Btn" color="var(--primary-light-color)">
                <span>Reset</span>
              </v-btn>
              <svg
                @click="closeOnContent = true"
                width="30"
                height="30"
                viewBox="0 0 30 30"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M22.5 7.5L7.5 22.5"
                  stroke="#063A06"
                  stroke-width="1.5"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
                <path
                  d="M7.5 7.5L22.5 22.5"
                  stroke="#063A06"
                  stroke-width="1.5"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                />
              </svg>
            </div>
          </v-list-item>

          <!-- Plan Subscription -->
          <v-list-item class="dropdown__list-item tag">
            <v-list-item-title class="tag-title"
              >Plan Subscription</v-list-item-title
            >
          </v-list-item>

          <!-- select  -->
          <v-list-item class="dropdown__list-item noHover pb-2">
            <div class="statusFilter">
              <v-checkbox
                label="Savings"
                color="var(--primary-color)"
                hide-details
                value="true"
              ></v-checkbox>
              <v-checkbox
                label="Jollification"
                color="var(--primary-color)"
                hide-details
                value="true"
              ></v-checkbox>
              <v-checkbox
                label="Investibox"
                color="var(--primary-color)"
                hide-details
                value="true"
              ></v-checkbox>
              <v-checkbox
                label="Loan"
                color="var(--primary-color)"
                hide-details
                value="true"
              ></v-checkbox>
            </div>
          </v-list-item>

          <!-- Wallet Balance -->
          <v-list-item class="dropdown__list-item tag">
            <v-list-item-title class="tag-title"
              >Wallet Balance</v-list-item-title
            >
          </v-list-item>

          <!-- select  -->
          <v-list-item class="dropdown__list-item noHover pb-2">
            <div class="statusFilter">
              <v-radio-group v-model="balance">
                <v-radio
                  color="var(--primary-color)"
                  label="₦0 - ₦100,000"
                  :value="0"
                ></v-radio>
                <v-radio
                  color="var(--primary-color)"
                  label="₦100,000 - ₦500,000"
                  :value="10"
                ></v-radio>
                <v-radio
                  color="var(--primary-color)"
                  label="₦500,000 and Above"
                  :value="100"
                ></v-radio>
                <v-radio
                  color="var(--primary-color)"
                  label="Custom"
                  value="custom"
                ></v-radio>
              </v-radio-group>
              <div class="minMax dateInput" v-if="balance == 'custom'">
                <input type="number" placeholder="Min(₦)" /><input
                  type="number"
                  placeholder="Max(₦)"
                />
              </div>
            </div>
          </v-list-item>

          <!-- Plan Status -->
          <v-list-item
            :class="{ 'm-0': balance != 'custom' }"
            class="dropdown__list-item tag"
          >
            <v-list-item-title class="tag-title">Plan Status</v-list-item-title>
          </v-list-item>

          <!-- select  -->
          <v-list-item class="dropdown__list-item noHover pb-2">
            <div class="statusFilter">
              <v-radio-group v-model="status">
                <v-radio
                  color="var(--primary-color)"
                  label="Active"
                  :value="0"
                ></v-radio>
                <v-radio
                  color="var(--primary-color)"
                  label="Inactive"
                  :value="10"
                ></v-radio>
              </v-radio-group>
            </div>
          </v-list-item>

          <!-- tag -->
          <v-list-item class="m-0 dropdown__list-item tag">
            <v-list-item-title class="tag-title">Date</v-list-item-title>
          </v-list-item>

          <!-- select  -->
          <v-list-item class="dropdown__list-item noHover pb-2">
            <div class="statusFilter dates">
              <div class="dateInput">
                <span class="label">From</span>
                <input type="date" name="" value="" />
              </div>
              <div class="dateInput">
                <span class="label">To</span>
                <input type="date" name="" value="" />
              </div>

              <v-btn color="var(--primary-color)" class="Btn"
                >Apply Filters</v-btn
              >
            </div>
          </v-list-item>
        </v-list>
      </v-menu>
      <v-btn color="var(--primary-color)" class="Btn">
        <span>Export</span>
        <svg
          width="14"
          height="9"
          viewBox="0 0 14 9"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M13 1L7 7L1 1"
            stroke="white"
            stroke-width="2"
            stroke-linecap="round"
          />
        </svg>
      </v-btn>
    </div>
  </div>
</template>

<script>
export default {
  props: ["placeholder"],
  data() {
    return {
      closeOnContent: false,
      dialog: false,
      balance: null,
      status: null,
    };
  },
};
</script>

<style lang="scss" scoped>
</style>