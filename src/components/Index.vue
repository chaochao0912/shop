<template>

    <el-container class="index">
      <!-- header部分 -->
  <el-header>
    <div class="logo">
      <img src="../assets/logo .png" alt="">
    </div>
    <div class="title">
      <h1>电商后台管理系统</h1>
    </div>

    <div class="logoout">
      <span>欢迎光临 ~</span>
      <a href="">退出</a>
    </div>
  </el-header>

  <el-container>
    <!-- 右边部分 -->
    <el-aside width="200px">
      <el-menu
      background-color="#545c64"
      text-color="#fff"
      active-text-color="#ffd04b">
      <el-submenu index="1">
        <template v-slot:title>
          <i class="el-icon-location"></i>
          <span>用户管理</span>
        </template>
          <el-menu-item index="1-1">
            <i class="el-icon-menu"></i>
        <span slot="title">用户列表</span>
          </el-menu-item>

      </el-submenu>
       <el-submenu index="2">
        <template v-slot:title>
          <i class="el-icon-location"></i>
          <span>权限管理</span>
        </template>
          <el-menu-item index="2-1">
            <i class="el-icon-menu"></i>
        <span slot="title">角色列表</span>
          </el-menu-item>
          <el-menu-item index="2-2">
            <i class="el-icon-menu"></i>
        <span slot="title">权限列表</span>
          </el-menu-item>
</el-submenu>
    </el-menu>
    </el-aside>

    <!-- main部分 -->
    <el-main>Main</el-main>
  </el-container>

</el-container>

</template>

<script>
export default {

}
</script>

<style lang="scss">
.index {
  height: 100%;
  // background-color: orange;

  .el-header{
    background-color: #d8d8d8;
    display: flex;
    .logo{
    height: 60px;
    width: 180px;
    img {
    margin:10px;
    height: 40px;
    }
  }
  .title{
    height: 60px;
    line-height: 60px;
    flex: 1;

    h1 {
      text-align: center;
      color:#545c64;
    }
  }
  .logoout{
    font-weight: 700;
    height: 60px;
    line-height: 60px;
    text-align: right;
    a {
      color:orange;
    }
  }
  }

  .el-aside{
    background-color: #545c64;
    .el-menu{
      border:none;
    }
  }
  .el-main{
    background-color: #ecf0f1;
  }

}
</style>
