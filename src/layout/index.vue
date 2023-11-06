<!-- 系统首页路由界面 -->
<template>
    <div class="layout_box">
      <!-- 左侧菜单 -->
      <div
        class="layout_left"
        :class="{ fold: LayOutSettingStore.fold ? true : false }"
      >
        <Logo></Logo>
        <!-- 滚动组件 -->
        <el-scrollbar class="scrollbar">
          <!-- 根据路由动态生成菜单 -->
          <el-menu
            :collapse="LayOutSettingStore.fold ? true : false"
            :collapse-transition="false"
            :default-active="$route.path"
            background-color="#001529"
            text-color="white"
          >
            <Menu :menuList="userStore.menuRoutes"></Menu>
          </el-menu>
        </el-scrollbar>
      </div>
      <!-- 顶部导航 -->
      <div
        class="layout_top"
        :class="{ fold: LayOutSettingStore.fold ? true : false }"
      >
        <Tabbar></Tabbar>
      </div>
      <!-- 中间内容 -->
      <div
        class="layout_main"
        :class="{ fold: LayOutSettingStore.fold ? true : false }"
      >
        <Main></Main>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  import { useRoute } from 'vue-router'
  import Logo from './logo/index.vue'
  import Menu from './menu/index.vue'
  import Tabbar from './tabbar/index.vue'
  import useUserStore from '@/store/modules/user'
  // 引入菜单内容
  import Main from './main/index.vue'
  import useLayOutSettingStore from '@/store/modules/setting'
  
  let userStore = useUserStore()
  // 获取路由对象
  let $route = useRoute()
  // 获取layout组件的配置
  let LayOutSettingStore = useLayOutSettingStore()
  </script>
  
  <script lang="ts">
  export default {
    name: 'Layout',
  }
  </script>
  
  <style lang="scss" scoped>
  .layout_box {
    width: 100%;
    height: 100vh;
  
    .layout_left {
      width: $base-menu-width;
      height: 100vh;
      color: white;
      background-color: $base-menu-background;
      transition: all 0.3s;
  
      .scrollbar {
        width: 100%;
        // color: white;
        height: calc(100vh - $base-menu-logo-height);
  
        .el-menu {
          // 去除menu菜单右侧边框
          border-right: none;
        }
      }
  
      &.fold {
        width: $base-menu-min-width;
      }
    }
  
    .layout_top {
      position: fixed;
      width: calc(100% - $base-menu-width);
      height: $base-tabbar-height;
      top: 0;
      left: $base-menu-width;
      transition: all 0.3s;
  
      &.fold {
        width: calc(100vw - $base-menu-min-width);
        left: $base-menu-min-width;
      }
    }
  
    .layout_main {
      position: absolute;
      width: calc(100% - $base-menu-width);
      height: calc(100vh - $base-tabbar-height);
      left: $base-menu-width;
      top: $base-tabbar-height;
      padding: 20px;
      overflow: auto;
      transition: all 0.3s;
  
      &.fold {
        width: calc(100vw - $base-menu-min-width);
        left: $base-menu-min-width;
      }
    }
  }
  </style>