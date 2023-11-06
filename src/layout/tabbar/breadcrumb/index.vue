<!--  -->
<template>
    <!-- 左侧导航 -->
    <div class="tabbar_left">
      <!-- 折叠菜单栏 -->
      <el-tooltip content="折叠菜单" placement="right">
        <el-icon :size="26" style="margin-right: 20px" @click="changIcon">
          <component
            :is="LayOutSettingStore.fold ? 'Fold' : 'Expand'"
          ></component>
        </el-icon>
      </el-tooltip>
      <!-- 面包屑导航栏 -->
      <el-breadcrumb separator-icon="ArrowRight">
        <el-breadcrumb-item
          v-for="(item, index) in $route.matched"
          :key="index"
          v-show="item.meta.title"
          :to="item.path"
        >
          <el-icon :size="14" style="verical-align: text-top">
            <component :is="item.meta.icon"></component>
          </el-icon>
          <span style="margin-left: 2px; font-size: 16px">
            {{ item.meta.title }}
          </span>
        </el-breadcrumb-item>
      </el-breadcrumb>
    </div>
  </template>
  
  <script setup lang="ts">
  import { useRoute } from 'vue-router'
  import useLayOutSettingStore from '@/store/modules/setting'
  
  let LayOutSettingStore = useLayOutSettingStore()
  let $route = useRoute()
  // 图标响应方法
  const changIcon = () => {
    LayOutSettingStore.fold = !LayOutSettingStore.fold
  }
  </script>
  
  <script lang="ts">
  export default {
    name: 'Breadcrumb',
  }
  </script>
  
  <style lang="scss" scoped>
  .tabbar_left {
    display: flex;
    align-items: center;
    margin-left: 20px;
  }
  </style>
  