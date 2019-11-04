<template>
  <section class="input-container">
    <i class="fas fa-check"></i>
    <div>
      <div>Choose a new Password</div>
      <form @submit.prevent="setNewPassword()">
        <input
          v-model="password"
          placeholder="Enter new password"
          @input="passwordCheck"
        />
        <p
          :class="{ 'formValidation--passed': password.length > 8 }"
          class="formValidation"
        >
          Longer than 8 characters
        </p>
        <p
          :class="{ 'formValidation--passed': has_uppercase }"
          class="formValidation"
        >
          Has a capital letter
        </p>
        <p
          :class="{ 'formValidation--passed': has_lowercase }"
          class="formValidation"
        >
          Has a lowercase letter
        </p>
        <p
          :class="{ 'formValidation--passed': has_number }"
          class="formValidation"
        >
          Has a number
        </p>
        <p
          :class="{ 'formValidation--passed': has_special }"
          class="formValidation"
        >
          Has a special character
        </p>
        <p
          :class="{ 'formValidation--passed': are_identic }"
          class="formValidation"
        >
          Both passwords are the same
        </p>
        <input
          v-model="passwordConfirmation"
          placeholder="Enter new Password"
          @input="passwordCheck"
        />
        <br />
      </form>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Startpage',
  data() {
    return {
      password: '',
      passwordConfirmation: '',
      has_number: false,
      has_lowercase: false,
      has_uppercase: false,
      has_special: false,
      are_identic: false
    }
  },
  methods: {
    passwordCheck() {
      this.has_number = /\d/.test(this.password)
      this.has_lowercase = /[a-z]/.test(this.password)
      this.has_uppercase = /[A-Z]/.test(this.password)
      this.has_special = /[!@#$%^&*)(+=._-]/.test(this.password)
      this.are_identic =
        this.password.localeCompare(this.passwordConfirmation) === 0
    }
  }
}
</script>
<style scoped>
.input-container {
  padding: 35px;
}
.formValidation {
  font-size: 13px;
  color: red;
}
.formValidation--passed {
  color: #0fa140;
}
</style>
