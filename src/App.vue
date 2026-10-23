<template>
  <div class="shell">
    <aside class="sidebar">
      <a class="brand" href="/">频率实验室<small>FREQUENCY / LEARN</small></a>
      <nav aria-label="组件通信示例">
        <router-link to="/parentPage_props"
          ><span>01</span> Props 向下传递</router-link
        ><router-link to="/parentPage_emit"
          ><span>02</span> Emit 向上通知</router-link
        >
      </nav>
      <a class="back-link" href="/">返回工作室</a>
    </aside>
    <main class="main">
      <header class="page-header">
        <p class="eyebrow">Vue 3 · Component Lab</p>
        <h1>让组件对话，亲手试一次。</h1>
        <p>
          修改消息，发送并观察另一侧状态。用两个可操作的小实验理解单向数据流。
        </p>
        <span class="status-label">本地交互 · 无需登录</span>
      </header>
      <div id="lesson-content" tabindex="-1"><router-view /></div>
    </main>
  </div>
</template>

<script>
import "./workbench.css";
export default { name: "App" };
</script>
