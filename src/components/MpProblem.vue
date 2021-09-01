<template>
  <div class="mp-problem">
    <div
      class="block-prb"
      v-for="(item, i) in img_path_chart[item_1][item_2]"
      v-bind:key="i"
    >
      <img
        class="image-prb"
        :src="require('../assets/' + item.path + '.png')"
      />
      <div id="description" v-html="item.text"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MpProblem",
  data() {
    return {
      item_1: 0,
      item_2: 0,
      first: ["fe-1", "fe-2", "fe-3"],
      img_path_chart: [
        [
          //1
          [
            //1-1
            {
              path: "e1-1-1",
              text: "财运多登录界面无隐私政策阅读提示",
            },
            {
              path: "e1-1-2",
              text: "4Can福罐隐私政策打开链接失效",
            },
            {
              path: "e1-1-3",
              text: "人人车隐私政策链接错误实际指向该小程序的主页",
            },
          ],
          [
            //1-2
            {
              path: "e1-2-1",
              text: "父母邦隐私政策无勾选框",
            },
            {
              path: "e1-2-2",
              text: "绍兴E网隐私政策默认勾选",
            },
          ],
          [
            //1-3
            {
              path: "e1-3-1",
              text: "妙汇商店隐私政策为用户协议的一部分且不完整",
            },
            {
              path: "e1-3-2",
              text: "九马汽车检测站隐私政策为模板生成使用对象为变量名替换",
            },
          ],
        ],
        [
          //2
          [
            //2-1
            {
              path: "e2-1-1",
              text: "皮皮虾出行未逐一列出个人信息的目的、方式、范围",
            },
            {
              path: "e2-1-2",
              text: "女士贴身衣橱未告知目的",
            },
          ],
          [
            //2-2
            {
              path: "e2-2-1",
              text: "罗博数码仅以改善服务质量、提升用户体验、定向推送信息、研发新产品等为由，强制要求用户同意收集个人信息",
            },
            {
              path: "e2-2-2",
              text: "数据统计工具京东良研超范围收集用户的定位信息",
            },
          ],
          [
            //2-3
            {
              path: "e2-3-1",
              text: "车有料隐私政策全文及小程序本身无删除、更正、投诉、举报的渠道",
            },
          ],
          [
            //2-4
            {
              path: "e2-4-1",
              text: "小燕在家数据存在跨境风险",
            },
            {
              path: "e2-4-2",
              text: "千里马招标网未经法律同意进行第三方共享",
            },
          ],
        ],
        [
          //3
          [
            //3-1
            {
              path: "e3-1-1",
              text: "隐私政策声明收集类型：个人注册信息,IP地址,网页记录",
            },
            {
              path: "e3-1-2",
              text: "实际收集类型：相册或相机,车信息,订阅授权,个人姓名,电话/手机号码,身份证,地址,购物,住址",
            },
          ],
          [
            //3-2
            {
              path: "e3-2-1",
              text: "班小二在隐私政策声明，不会收集用户的手机号码，但是在创建班级页面确有输入手机号码的填写框",
            },
          ],
        ],
        [
          //4
          [
            //4-1
            {
              path: "e4-1-1",
              text: "优衣库小程序通过request在未加密情况下发送用户位置信息1.调用获取位置信息的API2.创建发送对象t3.将位置信息附加到t中4.通过request发送数据",
            },
          ],
          [
            //4-2
            {
              path: "e4-2-1",
              text: "",
            },
          ],
        ],
      ],
    };
  },
  methods: {
    set_data: function (which) {
      this.item_1 = which.item_1;
      this.item_2 = which.item_2;
    },
  },
};
</script>

<style>
.block-prb {
  margin-left: 3%;
  float: left;
  width: 25%;
}
.mp-problem {
  width: 75%;
  margin-top: 50px;
  float: left;
}
</style>