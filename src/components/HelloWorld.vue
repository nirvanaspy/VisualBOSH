<template>
  <!--style="height: 100%"-->
  <div class="hello" style="height: 100%">
    <!-- navbar -->
    <!--style="height: 50px"-->
    <div class="navbar navbar-inverse" style="">
      <div class="navbar-inner" style="padding-top:10px;padding-bottom:10px">
        <button type="button" class="btn btn-navbar visible-phone" id="menu-toggler">
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
          <span class="icon-bar"></span>
        </button>
        <div class="brand">
          <!-- <img src="img/logo.png" /> -->
          <div style="float:left;width:30px;">
            <!-- <img src="img/ico-mail.png" /> -->
            <i class="icon-leaf" style="color:white;"></i>
          </div>

          <div style="float:right;">

            <h4 style="color:white;font-weight:700;">可视化部署工具</h4>
          </div>

        </div>
        <div class="login-out pull-right" @click="signout">
          <span class="text">退出</span>
          <i class="icon icon-user"></i>
        </div>
        <div class="goback pull-right" @click="gobackToProject">
          <span class="text">返回项目</span>
        </div>
      </div>
    </div>
    <!-- sidebar -->
    <!--style="background-color: #f8f8f8;top: 50px;bottom:0px"-->
    <div id="sidebar-nav" style="">
      <!--style="background-color: #f8f8f8;"-->
      <ul id="dashboard-menu" style="height:100%;">
        <li class="active">
          <router-link to="/users">
            <i class="icon-group"></i>
            <span>用户管理</span>
          </router-link>
        <!--  <div class="pointer"
          >
            <div class="arrow"></div>
            <div class="arrow_border"></div>
          </div>-->
          <!-- <a id="index.html">
            <i class="icon-home"></i>
            <span>Home</span>
          </a> -->
        </li>


        <li>
          <router-link to="/deploy">
            <i class="icon-sitemap"></i>
            <span>部署</span>
          </router-link>
        <!--  <div class="pointer">
            <div class="arrow"></div>
            <div class="arrow_border"></div>
          </div>-->
        </li>
       <li>
          <router-link to="/cfgroups">
            <i class="icon-book"></i>
            <span>集群纵览</span>
          </router-link>
        </li>
      </ul>
    </div>

    <!-- main container -->
    <div class="content" style="margin-top: 64px">
      <!-- 路由出口 -->
      <transition name="fade">
        <router-view></router-view>
      </transition>
    </div>
  </div>

</template>

<script>
/* eslint-disable */
export default {
  data () {
    return {
    }
  },
  mounted () {
    this.$nextTick(() => {
      $('html').niceScroll({
        /* autohidemode: 'cursor', */
        cursoropacitymax: 0
      })
    })
  },
  methods: {
    signout() {
      var msg = "您确定退出登录吗？";
      if (confirm(msg) == true){
        this.$router.push('/')
      }
    },
    gobackToProject() {
      var msg = "您确定返回项目选择吗？";
      if (confirm(msg) == true)
      this.$router.push('/selectProject')
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
 .fade-enter-active,.fade-leave-active{
    transition: all .3s ease;
  }
  .fade-enter,.fade-leave-to {
    opacity:0;
  }
  .login-out{
    position: relative;
    top:8px;
    right:22px;
    font-size: 18px;
    font-weight: 700;
    height:40px;
    color:#fff;
    cursor: pointer
  }
  .login-out .icon{
    font-size: 26px;
    margin-left:6px;
  }
  .goback{
    position: relative;
    top:13px;
    right:30px;
    font-size:18px;
    color:#fff;
    cursor: pointer;
    font-weight: 700;
  }
  .hello .navbar-inverse{
    position: fixed;
    top:0;
    z-index:1000;
    width:100%;
  }
  #sidebar-nav {
    position: fixed;
    top:64px;
    left:0;
    height:100%;
  }
 @media (max-width: 767px) {
   #sidebar-nav {
     left: -200px;
     position: fixed;
   }
   #sidebar-nav.display {
     position: absolute;
     left: 0;
     top:0;
     height: 100%;
   }
 }
 /* .fade-leave-to{
    transform: translate3d(30%,0,0);
  }*/
</style>
