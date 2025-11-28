<template>
  <n-config-provider :theme="theme">
    <n-loading-bar-provider>
      <n-dialog-provider>
        <n-notification-provider>
          <n-message-provider>
            <slot />
          </n-message-provider>
        </n-notification-provider>
      </n-dialog-provider>
    </n-loading-bar-provider>
  </n-config-provider>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { darkTheme, useModal, type GlobalTheme } from 'naive-ui'

// 可以根据需要切换主题
const theme = ref<GlobalTheme | null>(darkTheme)

// 如果需要暗色主题，可以这样设置：
// const theme = ref<GlobalTheme | null>(darkTheme)

// 挂载 naive 组件
const setupNaiveTools = () => {
  // 进度条
  window.$loadingBar = useLoadingBar()
  // 通知
  window.$notification = useNotification()
  // 信息
  window.$message = useMessage()
  // 对话框
  window.$dialog = useDialog()
  // 模态框
  window.$modal = useModal()
}
</script>
