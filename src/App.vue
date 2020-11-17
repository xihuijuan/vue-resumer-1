<template>
  <div id="app">
    <Topbar class="topbar" />
    <main>
      <Editor class="editor" />
      <Preview class="preview" />
    </main>
  </div>
</template>

<script>
import Topbar from "./components/Topbar";
import Editor from "./components/Editor";
import Preview from "./components/Preview";

export default {
  name: "App",
  components: {
    Topbar,
    Editor,
    Preview,
  },
};
</script>

<style lang="scss">
/* ie8以下都支持，要在app之上的每一个父元素上都加上100% */
html,
body,
#app {
  height: 100%;
  overflow: hidden;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* height: 100vh; ie8以下不支持*/
  display: flex;
  flex-direction: column;
}
.topbar {
}
main {
  
  display: flex;
  flex: 1;

  > .editor {
    width: 20em;
  }

  > .preview {
    flex: 1;
  }
}
</style>
