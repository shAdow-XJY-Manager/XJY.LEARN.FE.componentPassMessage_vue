<template>
  <section class="panel">
    <p class="panel-label">01 / CHILD</p>
    <h3>子组件 · 事件来源</h3>
    <label class="field-label" for="child-message">事件携带的消息</label
    ><input
      id="child-message"
      v-model="message"
      maxlength="160"
      @keyup.enter="!$event.isComposing && toParent()"
    />
    <div class="actions">
      <button class="primary" :disabled="!message.trim()" @click="toParent">
        发出事件
      </button>
    </div>
    <p class="feedback">事件名：passDataString</p>
    <code class="code">emit('passDataString', message)</code>
  </section>
</template>

<script>
export default {
  name: "childPage_emit",
  emits: ["passDataString"],
  data() {
    return { message: "子组件已完成任务。" };
  },
  methods: {
    toParent() {
      if (this.message.trim())
        this.$emit("passDataString", this.message.trim());
    },
  },
};
</script>
