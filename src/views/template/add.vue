<template>
  <div class="app-container">
    <!--可视化选择一个模板-->
    <el-alert
      title="请选择一个模板"
      type="success"
      show-icon>
    </el-alert>
      <div class="left_continer" v-for="item in templates" @click="addView">
        <el-tooltip placement="top">
          <div slot="content"><img :src="imgs[0]"/></div>
          <img :src="item.temp_img"/>
        </el-tooltip>
        <div class="left_item">
            <span>{{item.name}}</span><br>
            <span>{{item.scale}}{{item.desc}}</span>
        </div>
      </div>
  </div>
</template>

<script>
import { getList } from '@/api/table'
import img_ico from '@/assets/view_ico.png'
var datas = []
for (var i = 0; i < 100; i++) {
  datas.push(
    { code: i + 1, name: '互联网资源监控', temp_img: img_ico, scale: '16:9', desc: '1920x1086px' })
}
export default {
  data() {
    return {
      imgs: [img_ico, img_ico, img_ico],
      templates: datas,
      list: null,
      listLoading: true
    }
  },

  filters: {
    statusFilter(status) {
      const statusMap = {
        published: 'success',
        draft: 'gray',
        deleted: 'danger'
      }
      return statusMap[status]
    }
  },
  created() {
    this.fetchData()
  },
  methods: {
    fetchData() {
      this.listLoading = true
      getList(this.listQuery).then(response => {
        this.list = response.data.items
        this.listLoading = false
      })
    },
    addView() {
      this.$router.push({ path: '/template/modify', query: {} })
    }
  }
}
</script>
<style>
.left_continer {
  width: 155px;
  height: 155px;
  display: inline-block;
  border: 1px solid silver;
  text-align: center;
  margin: 10px;
  padding: 10px;
  border-radius: 5px;
  font-size: 12px;
  line-height: 18px;
  cursor: pointer;
}
.left_item {
  display: inline-table;
}
.left_continer img {
  width: 100%;
  height: 99px;
}
.temp_main {
  display: inline-block;
  background-color: deeppink;
}
</style>
