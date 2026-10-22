<template>
  <section class="panel">
    <p class="panel-label">02 / CHILD</p>
    <h3>子组件 · 接收结果</h3>
    <p class="muted">收到的 passDataString</p>
    <output class="value" aria-live="polite">{{
      passDataString || "等待父组件发送消息…"
    }}</output>
    <p class="feedback">
      {{ passDataString ? "已收到 · 内容与父组件一致" : "尚未收到消息" }}
    </p>
    <code class="code">props: { passDataString: String }</code>
  </section>
</template>

<script>
export default {
  name: "childPage_props",
  props: { passDataString: { type: String, required: true } },
};
</script>
