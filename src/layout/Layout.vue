<template>
  <a-layout id="components-layout-demo-fixed" class="layout">
    <a-layout-header :style="{height:'59px', background: '#fff', zIndex: 1, width: '100%' }">
      <div class="logo">
        <img src="../assets/logo.png" />
      </div>
      <menu-login />
      <simple-menu />
    </a-layout-header>
    <a-layout-content :style="{ padding: '0 25px', marginTop: '5px' }">
      <div :style="{ background: '#F0F2F5', padding: '14px', minHeight: '660px' }"><router-view /></div>
    </a-layout-content>
    <a-layout-footer :style="{marginBottom: '10px' , textAlign: 'center' }">
      Clms ©2020 Created by ZYT1 | 湘ICP备20004440号-1
    </a-layout-footer>
  </a-layout>
</template>

<script>
import SimpleMenu from './menu/Menu'
import MenuLogin from './menu/MenuLogin'
export default {
  components: { SimpleMenu, MenuLogin }
}
</script>

<style>
  #components-layout-demo-fixed .logo img {
    width: 80px;
    height: 31px;
    margin: 16px 14px 16px 0;
    float: left;
  }
</style>
