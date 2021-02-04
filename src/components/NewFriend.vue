<template>
  <form @submit.prevent="submitData">
    <div>
      <label>Name</label>
      <input
        type="text"
        v-model="enteredName"
        v-on:blur="handleBlurName"
        @change="nameChangeHandler"
      />
      <p v-if="nameError" style="color:red;">{{ nameError }}</p>
    </div>
    <div>
      <label>Phone</label>
      <input type="tel" v-model="enteredPhone" v-on:blur="handleBlurPhone" />
      <p v-if="phoneError" style="color:red;">{{ phoneError }}</p>
    </div>
    <div>
      <label>Email</label>
      <input type="email" v-model="enteredEmail" v-on:blur="handleBlurEmail" />
      <p v-if="emailError" style="color:red;">{{ emailError }}</p>
    </div>
    <div>
      <button>Add Contact</button>
    </div>
  </form>
</template>
<script>
export default {
  emits: ["add-contact"],
  data() {
    return {
      enteredName: "",
      enteredPhone: "",
      enteredEmail: "",
      nameError: "",
      phoneError: "",
      emailError: "",
    };
  },
  methods: {
    submitData() {
      if (!this.enteredName || !this.enteredEmail || !this.enteredPhone) {
        this.nameError = "Please Enter Name";
        this.phoneError = "Please Enter Phone Number";
        this.emailError = "Please Enter Email";
        return;
      } else {
        this.nameError = "";
        this.phoneError = "";
        this.emailError = "";
      }

      this.$emit(
        "add-contact",
        this.enteredName,
        this.enteredPhone,
        this.enteredEmail
      );
      this.enteredName = "";
      this.enteredPhone = "";
      this.enteredEmail = "";
    },
    handleBlurName() {
      if (!this.enteredName) {
        this.nameError = "Please Enter Name";
        return;
      } else {
        this.nameError = "";
      }
    },
    handleBlurPhone() {
      if (!this.enteredPhone) {
        this.phoneError = "Please Enter Phone Number";
        return;
      } else {
        this.phoneError = "";
      }
    },
    handleBlurEmail() {
      if (!this.enteredEmail) {
        this.emailError = "Please Enter Email";
        return;
      } else {
        this.emailError = "";
      }
    },
    nameChangeHandler() {
      //   if (!this.enteredName) {
      //     this.nameError = "Please Enter Name";
      //     return;
      //   } else {
      //     this.nameError = "";
      //   }
      // alert("Changing");
    },
  },
};
</script>
