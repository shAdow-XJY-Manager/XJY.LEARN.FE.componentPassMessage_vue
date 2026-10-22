<template>
  <section>
    <h2>Props：从父组件到子组件</h2>
    <p class="description">
      父组件持有数据，子组件通过声明的 prop
      接收。先编辑消息，再发送，观察右侧变化。
    </p>
    <div class="two-col">
      <section class="panel">
        <p class="panel-label">01 / PARENT</p>
        <h3>父组件 · 消息来源</h3>
        <label class="field-label" for="parent-message">发送内容</label
        ><input
          id="parent-message"
          v-model="draft"
          maxlength="160"
          @keyup.enter="!$event.isComposing && toChild()"
        />
        <div class="actions">
          <button class="primary" @click="toChild" :disabled="!draft.trim()">
            发送给子组件</button
          ><button class="quiet" @click="reset">重置</button>
        </div>
        <p class="feedback" role="status">
          {{
            count
              ? `已发送 ${count} 次，子组件已同步。`
              : "输入内容后点击发送。"
          }}
        </p>
        <code class="code">&lt;Child :passDataString="passData" /&gt;</code>
      </section>
      <ChildPage :passDataString="passData" />
    </div>
    <p class="note">
      数据向下传递：子组件展示收到的值，不直接修改父组件的数据。
    </p>
  </section>
</template>

<script>
import ChildPage from "./childPage_props.vue";
export default {
  name: "parentPage_props",
  components: { ChildPage },
  data() {
    return { draft: "你好，频率实验室。", passData: "", count: 0 };
  },
  methods: {
    toChild() {
      if (this.draft.trim()) {
        this.passData = this.draft.trim();
        this.count++;
      }
    },
    reset() {
      this.passData = "";
      this.count = 0;
      this.draft = "你好，频率实验室。";
    },
  },
};
</script>
