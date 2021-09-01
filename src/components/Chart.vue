<template>
  <div id="mainContent">
    <div class="echarts" ref="chart"></div>
  </div>
</template>

<script>
import * as echarts from "echarts";

export default {
  name: "Chart",
  props: ["which"],
  data() {
    return {
      chart_data: [
        [
          {
            item: [
              "个人信息收集使用规则难以访问",
              "有用户协议等相关规则，但是没有个人信息收集使用内容的",
              "首次打开、加载时五个人信息收集使用规则的阅读提示",
            ],
            digit: [38, 37, 419],
          },
          {
            item: [
              "用户表示不同意后仍频繁征求同意，或用户表示不同意后仍收集使用个人信息",
              "默认用户同意",
            ],
            digit: [5, 325],
          },
          {
            item: ["多产品使用同一份隐私政策", "隐私政策为用户协议的一部分"],
            digit: [173, 142],
          },
        ],
        [
          {
            item: [
              "申请个人敏感信息时，未同步告知用户其目的，或目的不明确、难以理解",
              "未逐一列出收集使用个人信息的目的、方式、范围等",
            ],
            digit: [188, 121],
          },
          {
            item: [
              "仅以改善服务质量、提升用户体验等为由，要求用户同意收集个人信息",
              "收集的个人信息类型与现有业务功能无关",
            ],
            digit: [24, 23],
          },
          {},
          {
            item: ["未经用户同意或法律许可，进行第三方共享", "含有不合理条款"],
            digit: [41, 14],
          },
        ],
        [
          {
            item: ["声明小于实际", "声明大于等于实际"],
            digit: [132, 138],
          },
          {},
        ],
        [
          {},
          {
            item: ["五个以上", "三到五个", "小于三个"],
            digit: [33, 87, 270],
          },
        ],
      ],
    };
  },
  methods: {
    draw_chart: function (which) {
      var chartDom = this.$refs.chart;
      if (echarts.getInstanceByDom(chartDom)) {
        echarts.dispose(chartDom);
      }
      var myChart = echarts.init(chartDom);

      var option;
      option = {
        title: {
          text: "世界人口总量",
          subtext: "数据来自网络",
        },
        tooltip: {
          trigger: "axis",
          axisPointer: {
            type: "shadow",
          },
        },
        grid: {
          left: "3%",
          right: "4%",
          bottom: "3%",
          containLabel: true,
        },
        xAxis: {
          type: "value",
          boundaryGap: [0, 0.01],
        },
        yAxis: {
          type: "category",
          data: this.chart_data[which.item_1][which.item_2].item,
        },
        series: [
          {
            type: "bar",
            data: this.chart_data[which.item_1][which.item_2].digit,
          },
        ],
      };

      option && myChart.setOption(option);
    },
  },
};
</script>

<style>
.echarts {
  float: left;
  width: 800px;
  height: 600px;
}
</style>