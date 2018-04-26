<template>
  <scroll-bar>
          <div v-for="item in list" >
            adfasdf
          </div>
  </scroll-bar>
</template>

<script>
import ScrollBar from '@/components/ScrollBar'
var datas = []
for (var i = 0; i < 77; i++) {
  datas.push({ a: i, b: 'adf' })
}
export default {
  components: { ScrollBar },
  data() {
    return {
      list: datas,
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
    }
  }
}
</script>
<style>
.div_scroll {
  width: 100%;
  height: 100%;
  background-color: blueviolet;
}
</style>
