<template>
  <div class="home">
    <el-button type="info" @click="quit">退出</el-button>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  methods: {
    quit: function() {
      window.sessionStorage.clear()
      this.$router.push('/login')
    }
  }
}
</script>
