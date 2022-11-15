<template>
  <div id="app">
    <router-view />
  </div>
</template>

<script>
import { generaMenu } from "./assets/js/menu";
export default {
  created() {
    // 刷新页面查询用户菜单
    // 每次刷新页面，都会去请求获取当前用户的菜单(及时生效权限)
    if (this.$store.state.userId != null) {
      generaMenu();
    }
    // 上传访客信息
    // 刷新一次，就上传一次访客记录
    this.axios.post("/api/report");
  }
};
</script>
