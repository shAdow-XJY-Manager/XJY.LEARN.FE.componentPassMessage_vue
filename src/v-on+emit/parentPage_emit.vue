<template>
  <section>
    <h2>Emit：从子组件到父组件</h2>
    <p class="description">
      子组件发出事件，父组件监听事件并更新自己的状态。编辑左侧消息，看看父组件如何响应。
    </p>
    <div class="two-col">
      <ChildPage @passDataString="updateFunction" />
      <section class="panel">
        <p class="panel-label">02 / PARENT</p>
        <h3>父组件 · 事件接收方</h3>
        <p class="muted">最新事件携带的数据</p>
        <output class="value" aria-live="polite">{{
          passData || "等待子组件发出事件…"
        }}</output>
        <p class="feedback" role="status">
          {{
            count
              ? `已收到 ${count} 次 passDataString 事件。`
              : "事件监听已就绪"
          }}
        </p>
        <code class="code"
          >&lt;Child @passDataString="updateFunction" /&gt;</code
        >
        <div class="actions">
          <button
            class="quiet"
            @click="
              passData = '';
              count = 0;
            "
          >
            清空接收记录
          </button>
        </div>
      </section>
    </div>
    <p class="note">
      事件向上通知：子组件描述发生了什么，父组件决定如何更新数据。
    </p>
  </section>
</template>

<script>
import ChildPage from "./childPage_emit.vue";
export default {
  name: "parentPage_emit",
  components: { ChildPage },
  data() {
    return { passData: "", count: 0 };
  },
  methods: {
    updateFunction(message) {
      this.passData = message;
      this.count++;
    },
  },
};
</script>
