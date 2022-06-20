<template>
  <div class="home_container">
    <el-menu
      default-active="1-4-1"
      class="el-menu-vertical-demo"
      @open="handleOpen"
      @close="handleClose"
      :collapse="isCollapse"
    >
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span slot="title">导航一</span>
        </template>
        <el-menu-item-group>
          <span slot="title">分组一</span>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
        <el-menu-item-group title="分组2">
          <el-menu-item index="1-3">选项3</el-menu-item>
        </el-menu-item-group>
        <el-submenu index="1-4">
          <span slot="title">选项4</span>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-menu-item index="2">
        <i class="el-icon-menu"></i>
        <span slot="title">导航二</span>
      </el-menu-item>
      <el-menu-item index="3" disabled>
        <i class="el-icon-document"></i>
        <span slot="title">导航三</span>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <span slot="title">导航四</span>
      </el-menu-item>
    </el-menu>

    <div class="main_container" :class="{ main_active: isCollapse }">
      <div class="main_header">
        <div class="left_box">
          <el-button
            type="primary"
            :icon="isCollapse ? 'el-icon-s-unfold' : 'el-icon-s-fold'"
            @click="isCollapse = !isCollapse"
          />
          <div class="breadcrumb_container">
            <el-breadcrumb separator="/">
              <el-breadcrumb-item :to="{ path: '/' }">首页</el-breadcrumb-item>
              <el-breadcrumb-item><a href="/">统计</a></el-breadcrumb-item>
            </el-breadcrumb>
          </div>
        </div>
        <ul class="right_container">
          <li>
            <span> 超级管理员 </span>
            <i class="el-icon-arrow-down"></i>
          </li>
          <li class="quit">退出</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isCollapse: false,
    };
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    },
  },
};
</script>

<style lang="less" scoped>
.home_container {
  position: relative;
  height: 100%;
  width: 100%;

  .el-menu {
    position: fixed;
    top: 0;
    left: 0;
    height: 100%;
    max-width: 200px;
  }

  .main_container {
    margin-left: 200px;
    transition: all 0.3s;

    &.main_active {
      margin-left: 65px;
    }

    .main_header {
      height: 50px;
      display: flex;
      padding: 0 20px;
      justify-content: space-between;
      border-bottom: 1px solid #eee;

      .left_box {
        display: flex;
        align-items: center;

        .breadcrumb_container {
          display: flex;
          align-items: center;
          margin-left: 10px;
        }
      }

      .right_container {
        text-align: center;
        cursor: pointer;

        li {
          line-height: 50px;
        }

        &:hover {
          .quit {
            display: block;
          }
        }

        .quit {
          display: none;
          padding: 0 25px;

          &:hover {
            background: #ccc;
            color: #999;
          }
        }
      }
    }
  }
}
</style>
