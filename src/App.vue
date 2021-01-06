<template>
  <div>
    <div>
      <button class="btn open" @click="display = true">点我，打开抽屉</button>
      <drawer
        title="Hello, I'm drawer"
        :display.sync="display"
        :width="drawerWidth"
        :drawerType="drawerType"
      >
        <p>1. Hello, world!</p>
        <p>2. Do you like it?</p>
        <button class="btn try" @click="changeWidth">点我试试?</button>
      </drawer>
    </div>

    <div class="tree-menu">
      <cTree :data="data"></cTree>
    </div>
  </div>
</template>
 
<script>
var myData = [
  {
    name: "Web秀",
    children: [
      {
        name: "web前端",
        children: [
          {
            name: "CSS",
          },
          {
            name: "JavaScript",
          },
          {
            name: "Vue",
          },
          {
            name: "小程序",
          },
          {
            name: "Three.js",
          },
        ],
      },
      {
        name: "服务器",
      },
      {
        name: "工具类",
      },
    ],
  },
  {
    name: "今日头条",
    children: [
      {
        name: "图片",
      },
      {
        name: "新闻",
        children: [],
      },
    ],
  },
  {
    name: "Angular",
  },
];
import drawer from "./components/drawer";
import cTree from "./components/tree";
export default {
  components: {
    cTree,
    drawer,
  },
  data() {
    return {
      data: myData,
      display: false,
      drawerWidth: "500px",
      drawerType: "right",
    };
  },
  methods: {
    changeWidth() {
      this.drawerWidth = this.drawerWidth === "500px" ? "800px" : "500px";
    },
  },
};
</script>
<style lang="scss">
#app {
  margin: 60px;
}
.btn {
  border: none;
  border-radius: 3px;
  outline: none;
  cursor: pointer;
  letter-spacing: 3px;
  &:hover {
    opacity: 0.8;
  }
  &.open {
    width: 200px;
    height: 80px;
    font-size: 18px;
    background-color: orange;
    color: #fff;
  }
  &.try {
    width: 100px;
    height: 40px;
    background-color: green;
    color: #fff;
    margin-top: 50px;
  }
}
</style>