<template>
  <div id="main">
    <h1>关于</h1>
    <p class="text">
      本报告针对小程序生态中的隐私安全问题进行了分析，从隐私权政策的规则展示和内容合规，以及行为一致性和安全风险，归纳了小程序存在四大类隐私安全风险。对来自微信、支付宝、百度等在内的7个平台的6069个小程序采取了自动化分析与人工审查相结合的评测
    </p>
    <div class="chart-content">
      <ChartContent />
    </div>
  </div>
</template>

<script>
import ChartContent from "./ChartContent.vue";

export default {
  name: "MainContent",
  components: {
    ChartContent,
  },
  data() {
    return {
      prb_data: [
        {
          path: "first_example_1.png",
          text: "快牙传文件<br />敏感信息泄露",
        },
        {
          path: "first_example_2.png",
          text: "汉堡王(京东小程序)<br />只有授权获得手机号码后才能查看隐私权政策",
        },
        {
          path: "first_example_3.png",
          text: "哈啰出行(支付宝小程序)<br />申请位置信息未告知目的，拒绝后仍频繁弹出申请",
        },
      ],
    };
  },
  // methods: {
  //   fun: function () {
  //     console.log(123);
  //   },
  // },
};
</script>

<style>
.chart-content {
  margin-top: 100px;
}
.text {
  font-size: 25px;
}
.prb-row {
  width: 90%;
  height: 800px;
}
.prb {
  float: left;
}
</style>