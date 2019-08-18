<template>
  <div v-if="isBreadcrumbShow">
    <el-breadcrumb separator="/">
      <el-breadcrumb-item
        v-for="(item, index) in breadcrumbData"
        :to="item.clickable ? item.path : ''"
        :key="index">
        {{ item.name }}
      </el-breadcrumb-item>
    </el-breadcrumb>
  </div>
</template>

<script>
import breadcrumbs from "./breadcrumb.config"

export default {
  name: 'Breadcrumb',

  computed: {
    isBreadcrumbShow () {
      return this.breadcrumbData && this.breadcrumbData.length && this.curBreadcrumb.isShow
    },

    breadcrumbData () {
      return this.$store.state.breadcrumb.breadcrumbData
    },

    curBreadcrumb () {
      return this.breadcrumbData.find(breadcrumb => breadcrumb.path === this.$route.path) || {}
    }
  }
}
</script>

<style lang="less">

</style>
