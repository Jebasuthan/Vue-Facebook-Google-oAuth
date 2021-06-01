<template>
  <div>
    <HomeMenu />
    <div class="main-container">
      <div class="loginsuccess-container">
        <h2 class="heading">Login Success!</h2>
        <div>
          <div v-if="this.$store.state.loginUser.loginType == 'fb'">
            <div class="center">
              <p>Welcome {{this.$store.state.loginUser.fb.user && this.$store.state.loginUser.fb.user.name}} !</p>
              <!-- <img :src="this.$store.state.loginUser.fb.user.name" /> -->
              <p><b>Facebook Access Token- </b>{{this.$store.state.loginUser.fb && this.$store.state.loginUser.fb.auth.accessToken}}</p>
            </div>
          </div>
          <div v-else-if="this.$store.state.loginUser.loginType == 'google'">
            <div class="center">
              <p>Welcome {{this.$store.state.loginUser.google.user.name}} !</p>
              <!-- <p>Email Address: {{this.$store.state.loginUser.google.user.email}} !</p> -->
              <img :src="this.$store.state.loginUser.google.user.profileImage" />
              <p><b>Google Access Token- </b>{{this.$store.state.loginUser.google.auth.access_token}}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import HomeMenu from '@/components/Menu'

export default {
  name: 'home',
  components: {
    HomeMenu
  }
}
</script>
