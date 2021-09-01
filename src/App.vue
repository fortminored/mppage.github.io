<template>
  <div id="app">
    <div id="BigBanner">
      <Banner />
    </div>

    <div id="content">
      <MainContent />
    </div>
  </div>
</template>

<script>
import Banner from "./components/Banner.vue";
import MainContent from "./components/MainContent.vue";

export default {
  name: "App",
  components: {
    Banner,
    MainContent,
  },
};
</script>

<style>
html,
body {
  margin: 0;
  padding: 0;
  background-color: #ebebeb;
  min-width: 1415px;
}
#BigBanner {
  background: linear-gradient(to right, rgb(0, 119, 255), rgb(0, 206, 110));
  height: 600px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  width: 100%;
}

#content {
  width: 80%;
  margin: 30px auto 30px auto;
}

.el-col {
  border-radius: 4px;
}
.bg-purple-dark {
  background: #99a9bf;
}
.bg-purple {
  background: #d3dce6;
}
.bg-purple-light {
  background: #e5e9f2;
}
.grid-content {
  border-radius: 4px;
  min-height: 36px;
}
.row-bg {
  padding: 10px 0;
  background-color: #f9fafc;
}
</style>
