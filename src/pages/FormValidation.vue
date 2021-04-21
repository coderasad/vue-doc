<template>
  <div id="form">
    <div class="container">
      <div class="row">
        <div class="col-6 offset-2">
          <div :class="{'show d-block' : showForm}" class="modal fade ">
            <div class="modal-dialog">
              <div class="modal-content">
                <div class="modal-header bg-info">
                  <h5 class="modal-title" id="exampleModalLabel">Vue Js SignUp Form Validation</h5>
                </div>
                <form @submit.prevent="handleFormSubmit">
                <div class="modal-body">
                    <div class="form-group">
                      <label for="email" class="col-form-label">Email Address</label>
                      <input v-model="email" type="text" class="form-control" id="email">
                      <div v-if="email" class="text-danger">{{ msg.email }}</div>
                    </div>
                    <div class="form-group">
                      <label for="password" class="col-form-label">Password</label>
                      <input autocomplete="off" v-model="password" type="password" class="form-control" id="password">
                      <div v-if="password" class="text-danger">{{ msg.password }}</div>
                    </div>
                    <div class="form-group">
                      <label for="confirm-password" class="col-form-label">Confirm Password</label>
                      <input v-model="confirmPassword" type="password" class="form-control" id="confirm-password">
                      <div v-if="confirmPassword" class="text-danger">{{ msg.confirmPassword }}</div>
                    </div>

                </div>
                <div class="p-3">
                  <button type="submit" :class="[button ? 'disabled' : '']" class="btn btn-primary">Sign Up</button>
                  <a @click.prevent="handleShowTerms" href="" class="float-end">Terms and Conditions</a>
                </div>
                </form>

                <h3 v-if="alert" class="alert bg-success text-light">Sign Up Successfully</h3>
              </div>
            </div>
          </div>
          <div :class="{'show d-block' : showTerms}" class="modal fade">
            <div class="modal-dialog">
              <div class="modal-content">
                <div class="modal-header bg-info">
                  <h5 class="modal-title" id="">Terms and Conditions</h5>
                </div>
                <div class="modal-body">
                  <ul class="list-group">
                    <li class="bg-light list-group-item px-3 py-2">Terms and Conditions#1</li>
                    <li class="bg-light list-group-item px-3 py-2">Terms and Conditions#2</li>
                    <li class="bg-light list-group-item px-3 py-2">Terms and Conditions#3</li>
                    <li class="bg-light list-group-item px-3 py-2">Terms and Conditions#4</li>
                  </ul>
                </div>
                <div class="p-3">
                  <button @click="handleShowForm" type="button" class="btn btn-primary">Back to Login</button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FormValidation",
  data() {
    return {
      showTerms: false,
      showForm: true,
      msg: [],
      email: '',
      password: '',
      confirmPassword: '',
      button: true,
      alert: false
    }
  },
  watch: {
    email(value) {
      this.email = value;
      this.checkEmail(value)
    },
    password(value) {
      this.password = value;
      this.checkPassword(value, 'password')
    },
    confirmPassword(value) {
      this.confirmPassword = value;
      this.checkConfirmPassword(value, 'confirmPassword');
      this.button = !(this.email && this.password && this.confirmPassword !== '');
    },
  },
  methods: {

    handleFormSubmit() {
      if(this.email && this.password && this.confirmPassword !== ''){
        this.alert = true
        setTimeout( () => {
          this.alert = false;
        },2000);
        this.email = '';
        this.password = '';
        this.confirmPassword = ''
      }
    },

    handleShowTerms() {
      this.showTerms = true;
      this.showForm = false;
    },
    handleShowForm() {
      this.showTerms = false;
      this.showForm = true;
    },
    checkEmail(value) {
      if (/\S+@\S+\.\S+/.test(value)) {
        this.msg['email'] = ''
      } else {
        this.msg['email'] = "Keep Typing... We are waiting for correct Email"
      }
    },
    checkPassword(value, password) {
      this.passwordLengthCheck(value, password)
    },
    checkConfirmPassword(value, confirmPassword) {
      this.passwordLengthCheck(value, confirmPassword);
      this.matchPassword(value, confirmPassword)

    },
    passwordLengthCheck(passwordToCheck, msg) {
      let remainingChars = 6 - passwordToCheck.length;
      if (passwordToCheck.length < 6) {
        this.msg[msg] = "Password must contain 6 characters." + remainingChars + "more to go..."
      } else {
        this.msg[msg] = ''
      }
    },
    matchPassword(value, msg) {
      if (value.length > 5) {
        if (value !== this.password) {
          this.msg[msg] = "Password does not match, please try again"
        } else {
          this.msg[msg] = ''
        }
      }
    },
  }
}
</script>

<style scoped>

</style>
