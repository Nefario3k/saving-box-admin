<template>
  <div>
    <h2>Personal Information</h2>
    <div class="dp-container d-flex">
      <img class="mt-0" src="images/profile-image.png" alt="profile image" />
      <div>
        <span class="d-block profile-name">Administrator</span>
        <button class="btn btn-primary">Update Photo</button>
      </div>
    </div>
    <section class="update-form mt-8">
      <div class="row">
        <div class="col-12 col-md-6">
          <form @submit.prevent="$emit('showSuccess')" class="row">
            <div class="col-12">
              <label for="adminFname" class="form-label label-design"
                >First Name</label
              >
              <input
                type="text"
                required
                class="form-control input-design"
                id="adminFname"
                placeholder="First name"
              />
            </div>
            <div class="col-12">
              <label for="adminLname" class="form-label label-design"
                >Last Name</label
              >
              <input
                type="text"
                required
                class="form-control input-design"
                id="adminLname"
                placeholder="Last name"
              />
            </div>
            <div class="col-12">
              <label for="adminEmailInput" class="form-label label-design"
                >Email</label
              >
              <input
                type="email"
                required
                class="form-control input-design"
                id="adminEmailInput"
                placeholder="johndoe@gmail.com"
              />
            </div>
            <div class="col-12">
              <label for="adminPhoneNumber" class="form-label label-design"
                >Phone Number</label
              >
              <input
                type="text"
                required
                class="form-control input-design"
                id="adminPhoneNumber"
                placeholder="234"
              />
            </div>
            <div style="justify-content: flex-end" class="d-flex col-12">
              <button type="submit" class="btn btn-primary btn-design">
                Save
              </button>
            </div>
          </form>
        </div>
      </div>
    </section>
  </div>
</template>
<script>
export default {
  data() {
    return {
      updatePassword: false,
      deleteAccount: false,
      switch1: false,
    };
  },
};
</script>
<style lang="scss" scoped>
div.dp-container {
  img {
    max-width: 98px;
    max-height: 98px;
    margin-top: 4rem;
  }

  .profile-name {
    font-size: 2.5rem;
    line-height: 2.15;
    color: var(--black);
  }

  button {
    width: 14rem;
    height: 4rem;
    font-size: 1.5rem;
    font-weight: 600;
  }
}

.account-options {
  margin-top: 6.7rem;

  h3 {
    color: var(--black);
    font-size: 2.5rem;
  }

  p {
    font-size: 1.8rem;
    margin: 0px;
  }

  p.fa2-intro {
    color: var(--gray-darken2);
  }

  .update-password {
    color: var(--primary-color);
  }

  .update-password + p {
    font-size: 1.4rem;
    color: var(--gray-darken1);
  }

  .delete-account {
    font-size: 1.4rem;
  }

  & > div {
    margin-bottom: 5rem;
  }
}
.btn-design {
  max-width: 20rem;
}
</style>