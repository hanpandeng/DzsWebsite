<template>
	<div id="app">
		<el-container>
			<!-- 顶部 -->
			<el-header style="height: auto;">
				<div class="logo">
					<img src="./assets/logo.png" alt="">
					<span>大樟树智能科技有限公司</span>
				</div>
			</el-header>
			<!-- 中部 -->
			<el-main>
				<router-view/>
			</el-main>
			<!-- 底部 -->
			<el-footer style="height: auto;" class="footer">
				<ul>
					<li>
						<i class="el-icon-phone-outline"></i>电话：17321019465
					</li>
					<li>
						<i class="el-icon-location-outline"></i>地址：上海市松江区中创路68号启迪漕河泾科技园
					</li>
				</ul>
				<el-row class="footer_row2">
					<el-col :xs="24">COPYRIGHT (©) 2017模板板块.</el-col>
				</el-row>
			</el-footer>
		</el-container>
		<!-- 返回顶部 -->
		<el-button size="mini" circle class="buttontop" @click="backTop" v-show="backTopShow">
			<i class="el-icon-upload2"></i>
		</el-button>
	</div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      backTopShow: false,
      logo: "/static/img/3917_jdbaq5ph(2).png",
      navshow: false
    };
  },
  methods: {
    backTop() {
      let back = setInterval(() => {
        if (document.body.scrollTop || document.documentElement.scrollTop) {
          document.body.scrollTop -= 100;
          document.documentElement.scrollTop -= 100;
        } else {
          clearInterval(back);
        }
      });
    },
    handleScroll() {
      if (document.documentElement.scrollTop + document.body.scrollTop > 100) {
        this.backTopShow = true;
      } else {
        this.backTopShow = false;
      }
    }
  },
  watch: {
    $route: {
      handler: function() {
        this.navshow = false;
      },
      // 深度观察监听
      deep: true
    }
  },
  mounted: function() {
    //挂载结束状态

    window.addEventListener("scroll", this.handleScroll);
    /* 加载完成在页面顶部 */
    this.$router.afterEach((to, from, next) => {
      window.scrollTo(0, 0);
    });
  }
};
</script>

<style>
body {
  margin: 0;
}

ul,
li,
ol {
  list-style: none;
  text-align: left;
}

a {
  text-decoration: none;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

a:-webkit-any-link {
  color: #000000;
}

.el-menu--horizontal > .el-menu-item.is-active {
  border-bottom: none;
}

/* herder */
.el-header {
  color: #333;
  text-align: center;
  line-height: 90px;
  box-sizing: border-box;
  overflow: hidden;
}
.logo {
  text-align: left;
  padding: 6px 0;
}
.logo img {
  max-width: 100px;
  max-height: 100px;
  vertical-align: middle;
}
.logo span {
  white-space: nowrap;
  font-size: 20px;
  color: #118545;
  font-weight: 600;
}

.header_nav {
  height: 90px;
}

.el-menu {
  padding-left: 50;
}

.header_nav ul {
  height: 100%;
  float: right;
}

.header_nav ul li {
  height: 100%;
}

.el-menu--horizontal > .el-menu-item,
.el-menu--horizontal > .el-submenu .el-submenu__title {
  height: 90px;
  line-height: 90px;
}

.el-menu.el-menu--horizontal {
  border-bottom: 0;
}

.el-menu--horizontal > .el-menu-item,
.el-menu--horizontal > .el-submenu {
  /* float: right; */
}

.mobel .el-menu {
  border-right: 0;
}

.mobel .el-menu > li {
  border-bottom: 1px solid #8cc5ff;
}

/* main */
.el-main {
  /* background-color: #E9EEF3; */
  color: #edf2fc;
  text-align: center;
  /* line-height: 90px; */
  padding: 0;
}

/* footer */
.footer {
  background-color: rgb(0, 68, 72);
  color: #f0f2f5;
  /* padding: 30px 30px; */
}

.footer_row2 {
  /* margin: 20px; */
  padding: 20px 20px;
  border-top: 1px solid #ebeef5;
}

/*  */
.buttontop {
  position: fixed;
  right: 50px;
  bottom: 50px;
}

.footer h3,
.footer a {
  color: #ffffff;
}
</style>
