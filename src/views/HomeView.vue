<template>
  <div class="home">
    <p>点击后1s会切换路由，但是dialog仍然存在</p>
    <t-button @click="onClick">点击触发bug</t-button>
    <t-dialog :visible.sync="visible" attach="body" destroyOnClose>
      <p>当前路由地址：{{path}}</p>
      <p>ps:路由地址没变化，说明了组件已经被销毁，但是DOM依然存在</p>
    </t-dialog>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  name: 'HomeView',
  data: () => {
    return {
      visible: false
    }
  },
  computed: {
    path () {
      return this.$route.path
    }
  },
  methods: {
    onClick () {
      this.visible = true
      setTimeout(() => {
        this.$router.push('/about')
      }, 1000)
    }
  }
})
</script>
