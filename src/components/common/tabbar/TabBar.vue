<template>
  <div id="tab-bar">
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "TabBar"
}
</script>

<style scoped>
#tab-bar{
  background-color: #ffffff;
  display: flex;
  border-top: 1px solid #eee;
  box-shadow: 0px -1px 1px rgba(150,150,150,.08);

  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 9;
}
</style>