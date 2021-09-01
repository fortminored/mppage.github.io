<template>
  <div class="def">
    <div>
      <img
        class="image-def"
        :src="require('../assets/' + img_path_def[item_1][item_2] + '.png')"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "Def",
  data() {
    return {
      item_1: 0,
      item_2: 0,
      img_path_def: [
        ["def1-1", "def1-2", "def1-3"],
        ["def2-1", "def2-2", "def2-3", "def2-4"],
        ["def3-1"],
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
.image-def {
  width: 800px;
  margin-top: 100px;
}
</style>