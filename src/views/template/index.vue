<template>
<div class="app-container" id="app">
  <el-container>
    <el-header>
      <el-row :gutter="20">
        <el-col :span="3">
          <el-button size="mini">打开</el-button>
          <el-button size="mini">新建</el-button>
        </el-col>
        <el-col :span="8" :offset="1">
          <div class="grid-content bg-purple">
            
            <el-button size="mini" @click="addItem">添加</el-button>
            <el-button size="mini">预览</el-button>
            <el-button size="mini">发布</el-button>
          </div>
        </el-col>
        <el-col :span="4"><div class="grid-content bg-purple">
          <el-button size="mini">预览</el-button>
          <el-button size="mini">发布</el-button>
          <el-button size="mini">帮助</el-button>
          </div>
        </el-col>
      </el-row>
    </el-header>
    <el-main>
  <grid-layout
            :layout="layout"
            :col-num="12"
            :row-height="30"
            :is-draggable="true"
            :is-resizable="true"
            :vertical-compact="true"
            :margin="[10, 10]"
            :use-css-transforms="true"
    >
        <grid-item v-for="item in layout" :x="item.x" :y="item.y" :w="item.w" :h="item.h" :i="item.i">
          复制、删除
            {{item.i}}
        </grid-item>
    </grid-layout>

    </el-main>
  </el-container>

  </div>
</template>

<script>
// 这个组件负责模板的构建、保存、修改
import VueGridLayout from "vue-grid-layout";

var GridLayout = VueGridLayout.GridLayout;
var GridItem = VueGridLayout.GridItem;

export default {
  name: "layoutgrid",
  components: {
    GridLayout,
    GridItem
  },
  data() {
    return {
      layout: [
        { x: 0, y: 0, w: 2, h: 2, i: "0" },
        { x: 2, y: 0, w: 2, h: 4, i: "1" },
        { x: 4, y: 0, w: 2, h: 5, i: "2" },
        { x: 6, y: 0, w: 2, h: 3, i: "3" },
        { x: 8, y: 0, w: 2, h: 3, i: "4" },
        { x: 10, y: 0, w: 2, h: 3, i: "5" },
        { x: 0, y: 5, w: 2, h: 3, i: "6" },
        { x: 2, y: 5, w: 2, h: 3, i: "7" },
        { x: 4, y: 5, w: 2, h: 3, i: "8" },
        { x: 6, y: 4, w: 2, h: 4, i: "9" },
        { x: 8, y: 4, w: 2, h: 4, i: "10" },
        { x: 10, y: 4, w: 2, h: 4, i: "11" },
        { x: 0, y: 10, w: 2, h: 2, i: "12" },
        { x: 2, y: 10, w: 2, h: 2, i: "13" },
        { x: 4, y: 8, w: 2, h: 2, i: "14" },
        { x: 6, y: 8, w: 2, h: 2, i: "15" },
        { x: 8, y: 10, w: 2, h: 2, i: "16" },
        { x: 10, y: 4, w: 2, h: 2, i: "17" },
        { x: 0, y: 9, w: 2, h: 3, i: "18" },
        { x: 2, y: 6, w: 2, h: 2, i: "19" }
      ],
      index: 0
    };
  },
  created() {
    // 创建初始化layout grid
    this.index = this.layout.length;
  },
  methods: {
    showPwd() {},
    addItem: function() {
      var item = {
        x: 0,
        y: 0,
        w: 2,
        h: 2,
        i: this.index + "",
        whatever: "bbb"
      };
      this.index++;
      this.layout.push(item);
    }
  }
};
</script>

<style>
div{
  border: 1px solid seagreen;
}
.vue-grid-item:not(.vue-grid-placeholder) {
  background: #ccc;
  border: 1px solid black;
}

.vue-grid-item.resizing {
  opacity: 0.9;
}

.vue-grid-item.static {
  background: #cce;
}

.vue-grid-item .text {
  font-size: 24px;
  text-align: center;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
  height: 100%;
  width: 100%;
}

.vue-grid-item .no-drag {
  height: 100%;
  width: 100%;
}

.vue-grid-item .minMax {
  font-size: 12px;
}

.vue-grid-item .add {
  cursor: pointer;
}

.vue-draggable-handle {
  position: absolute;
  width: 20px;
  height: 20px;
  top: 0;
  left: 0;
  background: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='10' height='10'><circle cx='5' cy='5' r='5' fill='#999999'/></svg>")
    no-repeat;
  background-position: bottom right;
  padding: 0 8px 8px 0;
  background-repeat: no-repeat;
  background-origin: content-box;
  box-sizing: border-box;
  cursor: pointer;
}

.el-header,
.el-footer {
  background-color: #b3c0d1;
  color: #333;
  text-align: center;
  line-height: 60px;
}

.el-aside {
  background-color: #d3dce6;
  color: #333;
  text-align: center;
  line-height: 200px;
}

.el-main {
  background-color: #e9eef3;
  color: #333;
  text-align: center;
}

body > .el-container {
  margin-bottom: 40px;
}

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
}
</style>