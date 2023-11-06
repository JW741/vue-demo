<template>
    <div class="tabbar">
        <div class="tabbar_left">
            <Breadcrumb />
        </div>
        <div class="tabbar_right">
            <Setting />
        </div>
    </div>
</template>

<script setup lang="ts">
import Breadcrumb from './breadcrumb/index.vue'
import Setting from './setting/index.vue';
</script>
<script lang="ts">
export default {
    name: "Tabbar"
}
</script>
<style scoped lang="scss">
.tabbar {
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: space-between;
    background-image: linear-gradient(
    to right,
    rgb(238, 232, 232),
    rgb(148, 122, 122),
    rgb(244, 167, 167)
  );

    .tabbar_left {
        display: flex;
        align-items: center;
        margin-left: 20px;

    }

    .tabbar_right {
        display: flex;
        align-items: center;
    }
}
</style>