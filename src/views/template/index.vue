<template>
  <div class="app-container" id="app">
    <el-row :gutter="20">
      <el-col :span="1"><div class="grid-content bg-purple">&nbsp;</div></el-col>
      <el-col :span="8">
        <div class="grid-content bg-purple">
               <el-button size="mini">预览</el-button>
        <el-button size="mini">发布</el-button>
        </div>
      </el-col>
      <el-col :span="4"><div class="grid-content bg-purple"></div></el-col>
      <el-col :span="4"><div class="grid-content bg-purple">
        <el-button size="mini">预览</el-button>
        <el-button size="mini">发布</el-button>
        <el-badge :value="100" :max="10" class="item">
          <el-button size="small">消息</el-button>
        </el-badge>
        </div>
      </el-col>
    </el-row>
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
            {{item.i}}
        </grid-item>
    </grid-layout>
    <el-button type="primary" >Create</el-button>
  </div>
</template>

<script>
// 这个组件负责模板的构建、保存、修改

import VueGridLayout from 'vue-grid-layout'

var GridLayout = VueGridLayout.GridLayout
var GridItem = VueGridLayout.GridItem

export default {
  name: 'layoutgrid',
  components: {
    GridLayout,
    GridItem
  },
  data() {
    return {
      layout: [
        { x: 0, y: 0, w: 2, h: 2, i: '0' }
      ]
    }
  },
  created() {
    // 创建初始化layout grid
  },
  methods: {
    showPwd() {}
  }
}
</script>

<style>
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
</style>
