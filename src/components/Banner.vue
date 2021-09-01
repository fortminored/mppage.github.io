<template>
  <div id="banner">
    <div class="h1">{{ title }}</div>
    <div class="h2">{{ subTitle }}</div>
    <img
      id="img-jiaoda"
      class="logo"
      alt="Xi'an Jiaotong Univeristy"
      src="../assets/jiaoda.png"
    />
    <div class="button-field">
      <a class="a" href="https://aclanthology.org/2021.acl-long.180/">
        <button class="button">
          <div class="inButton">全文下载</div>
        </button>
      </a>
      <a class="a" href="https://aclanthology.org/2021.acl-long.180/">
        <button class="button">
          <div class="inButton">数据集下载</div>
        </button> </a
      ><a class="a" href="https://aclanthology.org/2021.acl-long.180/">
        <button class="button">
          <div class="inButton">更多信息</div>
        </button>
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: "Banner",
  data() {
    return {
      title: "小程序隐私安全风险报告",
      subTitle:
        "research on privacy statement of miniprogram & dataflow analysis tool for miniprogram",
    };
  },
};
</script>

<style>
#banner {
  width: 100%;
  height: 55%;
  color: #ffffff;
  font-family: "Lato, Arial, sans-serif";
  padding-top: 30px;
  letter-spacing: 0.005em;
  line-height: 1.5;
}
.h1 {
  width: 80%;
  font-size: 100px;
  font-weight: 90;
  text-align: center;
  margin: auto;
  padding: 0px;
}

.h2 {
  width: 80%;
  font-size: 40px;
  font-weight: 100;
  text-align: center;
  margin: 0 auto 0 auto;
  padding: 0px;
}

.logo {
  float: left;
  top: 5px;
  position: absolute;
}

#img-jiaoda {
  left: 10px;
  top: 30px;
  width: 240px;
}
.inButton {
  text-align: center;
  font-size: 25px;
  color: white;
  padding: 20px;
}
.button {
  width: 20%;
  border-radius: 4px;
  border-style: solid;
  border-width: 1px;
  border-color: white;
  float: left;
  margin-left: 10%;
  background-color: transparent;
  opacity: 0.9;
}
.a :hover {
  border-width: 3px;
  opacity: 1;
}
.a {
  text-decoration: none;
}
.button-field {
  margin-top: 100px;
}
</style>