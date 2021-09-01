<template>
  <div>
    <h1>小程序隐私政策相关问题示例</h1>
    <div class="pane">
      <div class="top">
        <div class="top-button-chart">
          <div
            v-for="(item, k) in top_button_data"
            v-bind:key="k"
            v-on:click="set_item_1(k)"
            :class="[
              { 'top-button': item_1 != k },
              { 'top-selected': item_1 == k },
            ]"
          >
            {{ item }}
          </div>
        </div>
      </div>

      <div class="side-button-chart">
        <div
          class="side-button"
          v-for="(item, i) in side_button_data.title[item_1]"
          v-bind:key="item"
        >
          <div class="side-button-text" v-on:click="set_item_2(i)">
            {{ item }}
          </div>
          <div
            v-bind:class="[
              { 'side-selected': j == item_3 },
              { 'sub-item': j != item_3 },
            ]"
            v-for="(item, j) in cur_item"
            v-bind:key="item"
            v-show="item_2 == i"
          >
            <div class="side-item-text" v-on:click="set_item_3(j)">
              {{ item }}
            </div>
          </div>
        </div>
      </div>
      <MpProblem ref="prb" v-if="show_prb" />
      <Chart ref="ch" v-if="show_chart" />
      <Def ref="def" v-if="show_def" />
    </div>
  </div>
</template>

<script>
import Chart from "./Chart.vue";
import Def from "./Def.vue";
import MpProblem from "./MpProblem.vue";
export default {
  name: "ChartContent",
  components: {
    Chart,
    MpProblem,
    Def,
  },
  data() {
    return {
      item_1: 0,
      item_2: 0,
      item_3: 0,
      top_button_data: ["规则展示", "内容合规", "行为一致", "安全风险"],
      side_button_data: {
        title: [
          ["公开性", "自愿性", "独立性"],
          ["清晰性", "必要性", "删除更正与投诉举报", "保留分享与权责要求"],
          ["声明收集范围与实际收集范围一致性", "违反使用规则收集使用信息"],
          ["传输未加密", "第三方库"],
        ],
        item: {
          common: ["定义与标准", "问题示例", "数据统计"],
          only_example: ["问题示例"], //4.1  3.2
          no_std: ["问题示例", "数据统计"], //4.2
          no_dat: ["定义与标准", "问题示例"], //2.3
        },
      },
    };
  },
  computed: {
    cur_item: function () {
      if (this.test_item([3, 0]) || this.test_item([2, 1])) {
        return this.side_button_data.item.only_example;
      }
      if (this.test_item([3, 1])) {
        return this.side_button_data.item.no_std;
      }
      if (this.test_item([1, 2])) {
        console.log("test");
        return this.side_button_data.item.no_dat;
      }
      return this.side_button_data.item.common;
    },
    show_chart: function () {
      if (this.test_item([3, 1]) && this.item_3 == 1) {
        return true;
      }
      if (
        this.test_item([3, 0]) ||
        this.test_item([2, 1]) ||
        this.test_item([1, 2])
      ) {
        return false;
      }
      if (this.item_3 == 2) {
        return true;
      }
      return false;
    },

    show_prb: function () {
      if (
        this.test_item([3, 0]) ||
        this.test_item([2, 1]) ||
        this.test_item([3, 1])
      ) {
        if (this.item_3 == 0) return true;
        return false;
      }
      if (this.item_3 == 1) return true;
      return false;
    },
    show_def: function () {
      if (this.test_item([3, 0]) || this.test_item([2, 1])) {
        return false;
      }
      if (this.test_item([3, 1])) {
        return false;
      }
      if (this.item_3 == 0) {
        return true;
      }
      return false;
    },
  },
  methods: {
    test_item: function (li) {
      if (li[0] == this.item_1 && li[1] == this.item_2) {
        return true;
      }
      return false;
    },
    set_item_1: function (item) {
      this.item_1 = item;
      this.set_item_2(0);
    },
    set_item_2: function (item) {
      this.item_2 = item;
      this.set_item_3(0);
      console.log("set2", this.item_1, this.item_2, this.item_3);
    },
    set_item_3: function (item) {
      this.item_3 = item;
      if (this.show_chart) {
        this.$nextTick(() => {
          this.$refs.ch.draw_chart({
            item_1: this.item_1,
            item_2: this.item_2,
          });
        });
      }
      if (this.show_prb) {
        this.$nextTick(() => {
          this.$refs.prb.set_data({
            item_1: this.item_1,
            item_2: this.item_2,
          });
        });
      }
      if (this.show_def) {
        this.$nextTick(() => {
          this.$refs.def.set_data({
            item_1: this.item_1,
            item_2: this.item_2,
          });
        });
      }
      console.log("set3", this.item_1, this.item_2, this.item_3);
    },
  },
};
</script>

<style>
.pane {
  width: 100%;
  height: 800px;
}
.top {
  height: 20%;
  width: 100%;
}
.top-button-chart {
  float: right;
  height: 160px;
  width: 80%;
  border-width: 0 0 1px 0;
  border-style: solid;
}
.top-button-chart > .top-button,
.top-button-chart > .top-selected {
  width: 20%;
  margin-left: 5%;
  margin-top: 50px;
  float: left;
  background-color: transparent;
  font-size: 30px;
  cursor: pointer;
}
.top-button {
  text-decoration-line: none;
}
.top-selected {
  text-decoration-line: underline;
}

.side-button-chart {
  width: 20%;
  height: 75%;
  border-width: 0 1px 0 0;
  border-style: solid;
  float: left;
}
.side-button {
  width: 100%;
  float: right;
  margin-bottom: 50px;
  background-color: transparent;
  border: transparent;
  font-size: 30px;
  font-weight: 600;
}
.side-button-text {
  cursor: pointer;
}
.side-button > .sub-item,
.side-button > .side-selected {
  width: 100%;
  float: right;
  margin-top: 25px;
  margin-bottom: 25px;
  font-size: 20px;
}
.sub-item {
  font-weight: 100;
}
.side-selected {
  font-weight: 400;
  text-decoration-line: underline;
}
.side-item-text {
  cursor: pointer;
}
</style>