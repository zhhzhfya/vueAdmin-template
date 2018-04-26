<template>
  <!--我的可视化-->
  <div>
    <div class="view_item" style="1px dashed;clear:both;" @click="addView">
      <img :src="imgs[0]" />
      <div>新建可视化</div>
      <!-- <div class="item_btns">
        <el-button-group>
          <el-button type="primary" size="mini" icon="el-icon-edit"></el-button>
          <el-button type="primary" size="mini" icon="el-icon-share"></el-button>
          <el-button type="primary" size="mini" icon="el-icon-delete"></el-button>
        </el-button-group>
      </div> -->
    </div>
    <div class="view_item" v-for="item in items" @click="modifyView">
      <img :src="item.src" />
      <div>{{item.name}}</div>
      <div class="item_btns">
        <el-button-group>
          <el-button type="primary" size="mini" icon="el-icon-edit"></el-button>
          <el-button type="primary" size="mini" icon="el-icon-share"></el-button>
          <el-button type="primary" size="mini" icon="el-icon-delete"></el-button>
        </el-button-group>
      </div>
    </div>
  </div>
</template>

<script>
import { getList } from '@/api/table'
import img_ico from '@/assets/view_ico.png'
import img_add from '@/assets/view_add.png'
export default {
  data() {
    return {
      list: null,
      listLoading: true,
      imgs: [img_add, img_add, img_add],
      items: [
        { code: '1', name: 'test1', src: img_ico, createtime: '2017-09-11' },
        { code: '2', name: 'test1', src: img_ico, createtime: '2017-09-11' },
        { code: '3', name: 'test1', src: img_ico, createtime: '2017-09-11' },
        { code: '4', name: 'test1', src: img_ico, createtime: '2017-09-11' }
      ]
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
      this.$router.push({ path: '/template/add', query: { viewId: 123 } })
    },
    modifyView() {
      this.$router.push({ path: '/template/modify', query: { viewId: 123 } })
    }
  }
}
</script>
<style>
.view_item {
  cursor: pointer;
  display: inline-grid;
  width: 200px;
  height: 250px;
  border: 1px solid rgb(192, 189, 189);
  margin: 10px 10px;
  border-radius: 8px;
  padding: 8px;
}

.item_btns {
  text-align: center;
}
.view_item img {
  width: 100%;
  height: 170px;
  border: 0px solid silver;
}
</style>
