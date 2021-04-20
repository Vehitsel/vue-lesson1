<template>
  <div id="app">
    <div class="app-content">
      <div id="nav">
          <router-link to="/">Home</router-link> |
          <router-link to="/about">About</router-link>
          <h2 class="title">
            <!-- {{message}} -->
            {{$route.meta.title}}
          </h2>
          <input type="text" v-model="message">
      </div>
      <router-view/>
    </div>
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/> -->
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {},
  data: () => ({
    message: 'Message'
  }),
}
</script>

<style lang="scss">
body {
 display: block;
 margin: 0;
 height: 100vh;
 width: 100vw;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  flex-flow: row nowrap;
  align-items: flex-start;
  justify-content: center;
  background: #2c3e50;
  padding: 30px;
  height: 100%;
  .app-content {
    margin-top: 10vh;
    width: 100%;
    max-width: 600px;
    background: white;
    border-radius: 16px;
    padding: 16px;
    #nav {
      a {
        font-weight: bold;
        color: #2c3e50;
        &.router-link-exact-active {
          color: #42b983;
        }
      }
    }
  }
}


</style>
