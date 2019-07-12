<template>
  <el-container id="rr">
    <el-aside :width="sff?'64px':'200px'" id="mm">
      <span class="aaw" :class="{bbw:sff}"></span>
      <el-menu
        default-active="1"
        class="el-menu-vertical-demo"
        background-color="#002033"
        text-color="#fff"
        active-text-color="#ffd04b"
        :collapse="sff"
        :collapse-transition='false'
      >
        <el-menu-item index="1">
          <i class="el-icon-s-home"></i>
          <span slot="title">首页</span>
        </el-menu-item>
        <el-menu-item index="2">
          <i class="el-icon-document"></i>
          <span slot="title">内容管理</span>
        </el-menu-item>
        <el-menu-item index="3">
          <i class="el-icon-picture"></i>
          <span slot="title">素材管理</span>
        </el-menu-item>
        <el-menu-item index="4">
          <i class="el-icon-s-promotion"></i>
          <span slot="title">发布文章</span>
        </el-menu-item>
        <el-menu-item index="5">
          <i class="el-icon-chat-dot-round"></i>
          <span slot="title">评论管理</span>
        </el-menu-item>
        <el-menu-item index="6">
          <i class="el-icon-present"></i>
          <span slot="title">粉丝管理</span>
        </el-menu-item>
        <el-menu-item index="7">
          <i class="el-icon-setting"></i>
          <span slot="title">个人设置</span>
        </el-menu-item>
      </el-menu>
    </el-aside>
    <el-container>
      <el-header class="myheader">
        <span @click="sf" class="el-icon-s-fold" style="font-size:'500px'"></span>
        <span id="text">江苏传智播客教育科技有限公司</span>

        <el-dropdown class="righth">
          <span class="el-dropdown-link">
            <img src="../assets/images/avatar.jpg" alt />
            <b>黑马小哥</b>
            <i class="el-icon-arrow-down el-icon--right"></i>
          </span>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item icon="el-icon-setting">个人设置</el-dropdown-item>
            <el-dropdown-item icon="el-icon-lock">退出登录</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
      </el-header>
      <el-main>
        <img src="../assets/images/welcome.jpg" alt="">
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
export default {
  data () {
    return {
      sff: false,
      sfff: '200px'
    }
  },
  methods: {
    sf () {
      this.sff = !this.sff
    }
  }
}
</script>

<style>
.myheader {
  border-bottom: 1px solid #ddd;
  line-height: 60px;
}
.myheader .el-icon-s-fold {
  font-size: 25px;
  vertical-align: middle;
}
.myheader #text {
  vertical-align: middle;
  margin-left: 10px;
}
.righth {
  float: right;
}
.el-dropdown-link img {
  vertical-align: middle;
  width: 30px;
  height: 30px;
  margin-right: 5px;
}
.aaw {
  display: block;
  width: 100%;
  height: 60px;
  background: #002840 url("../assets/images/logo_admin.png") no-repeat center/140px auto;
}
.bbw{
 display: block;
  width: 100%;
  height: 60px;
  background: #002840 url("../assets/images/logo_admin_01.png") no-repeat center;
}
#mm {
  background-color: #002033;
  height: 100%;
  color: azure;
}
#rr {
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 100%;
}
.el-menu-vertical-demo {
  border-right: none;
}
</style>
