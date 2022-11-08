<template>
  <div style="padding: 20px">
    <a-badge status="success" text="启用" />
    <a-table :columns="columns" :data="data" />
  </div>
</template>

<script setup lang="jsx">
import { reactive, toRefs } from 'vue'
const state = reactive({
  columns: [
    {
      title: '用户昵称',
      dataIndex: 'nickName',
      width: 150
    },
    {
      title: '状态',
      dataIndex: 'status',
      width: 100,
      render: ({ record }) => {
        switch (record.status) {
          case 0:
            return <a-badge status="success" text="启用" />
          case 1:
            return <a-badge status="danger" text="禁用" />
        }
      }
    }
  ],
  data: [
    { nickName: '测试', status: 0 }
  ]
})

const { columns, data } = toRefs(state)
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
