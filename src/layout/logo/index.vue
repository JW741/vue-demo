<!-- logo -->
<template>
    <div class="logo" v-if="setting.logoHidden">
      <img :src="setting.logo" alt="" />
      <p :class="{ fold: LayOutSettingStore.fold ? true : false }">{{ setting.title }}</p>
    </div>
  </template>
  
  <script setup lang="ts">
  import setting from '@/setting'
  </script>
  
  <script lang="ts">
  export default {
    name: 'Logo',
  }
  import useLayOutSettingStore from '@/store/modules/setting'
  let LayOutSettingStore = useLayOutSettingStore()
  </script>
  
  <style lang="scss" scoped>
  .logo {
    width: 100%;
    height: $base-menu-logo-height;
    color: #e4a4a4;
    display: flex;
    align-items: center;
    padding: 10px;
    img {
      width: 40px;
      height: 40px;
      border-radius: 50%;
    }
    p {
      font-size: $base-logo-title-fontSize;
      margin-left: 20px;
      white-space: nowrap;
      transition: all 0.3s;
      &.fold {
        overflow: hidden;
      }
    }
  }
  </style>
  