<template>
  <div class="login">
    <div class="container-fluid">
      <div>
        <img src="../assets/red-logo.png" height="200">
        <p>
          <strong>Please sign up or login to continue.</strong>
        </p>
        <button type="button" class="btn btn-lg signUpBtn m-2" data-toggle="modal" data-target="#signUp">
          <b>Sign Up</b>
        </button>
        <button type="button" class="btn btn-lg loginBtn m-2" data-toggle="modal" data-target="#login">
          <b>Login</b>
        </button>
      </div>
      <div>
        <!-- Sign Up Modal Start -->
        <div class="modal fade" id="signUp" tabindex="-1" role="dialog">
          <div class="modal-dialog modal-dialog-centered" role="document">
            <div class="modal-content">
              <form @submit.prevent="createUser(createdUser)">
                <div class="modal-body">
                  <!-- username input -->
                  <div class="m-2">
                    <i class="fas mar-right fa-1x fa-user"></i>
                    <input type="text" name="username" v-model="createdUser.userName" placeholder=" Username" required>
                  </div>
                  <div class="m-2">
                    <i class="far mar-right fa-1x fa-envelope"></i>
                    <input type="email" name="userEmail" v-model="createdUser.email" placeholder="Email" required>
                  </div>
                  <div class="m-2">
                    <i class="far mar-right fa-1x fa-edit"></i>
                    <input type="password" name="password" v-model="createdUser.password" placeholder=" Password">
                  </div>
                </div>
                <div class="modal-footer">
                  <button type="submit" class="btn btn-lg submitBtn">
                    <b>Create User</b>
                  </button>
                  <button type="button" class="btn btn-lg btn-secondary" data-dismiss="modal">
                    <b>close</b>
                  </button>
                </div>
              </form>
            </div>
          </div>
        </div>
        <!-- Login Modal Start -->
        <div class="modal fade" id="login" tabindex="-1" role="dialog">
          <div class="modal-dialog modal-dialog-centered" role="document">
            <div class="modal-content">
              <form @submit.prevent="login(user)">
                <div class="modal-body">
                  <div class="m-2">
                    <i class="far mar-right fa-1x fa-envelope"></i>
                    <input type="text" name="userEmail" v-model="user.email" placeholder=" Email" required>
                  </div>
                  <div class="m-2">
                    <i class="far mar-right fa-1x fa-edit"></i>
                    <input type="password" name="password" v-model="user.password" placeholder=" Password">
                  </div>
                </div>
                <div class="modal-footer">
                  <button type="submit" class="btn btn-lg submitBtn">
                    <b>Login</b>
                  </button>
                  <button type="button" class="btn btn-lg btn-secondary" data-dismiss="modal">
                    <b>close</b>
                  </button>
                </div>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>
  export default {
    name: 'Login',
    data() {
      return {
        user: {},
        createdUser: {}
      }
    },
    methods: {
      login() {
        this.$store.dispatch('login', this.user)
        $('#login').modal('hide')
      },
      createUser() {
        this.$store.dispatch('createUser', this.createdUser)
        $('#signup').modal('hide')
      }
    }
  }
</script>


<style scoped>
  p {
    padding-top: 16px
  }

  .modal-body {
    color: black
  }

  .login {
    background-color: #C15253;
    height: 100vh;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
  }

  .signUpBtn {
    background-color: rgb(154, 218, 181);
    color: whitesmoke;
    text-align: center;
    width: 110px
  }
  .signUpBtn:hover{
    background-color: rgba(154, 218, 181, .75)
  }

  .loginBtn {
    background-color: rgb(240, 198, 148);
    color: whitesmoke;
    text-align: center;
    width: 110px;
  }
  .loginBtn:hover{
    background-color: rgba(240, 198, 148, .75)
  }
  .submitBtn {
    background-color: rgb(193, 82, 84);
    color: whitesmoke;
  }
  .submitBtn:hover{
    background-color: rgba(193, 82, 84, .75)

  }
</style>