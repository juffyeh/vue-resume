<template>
  <div id="app" v-bind:class="{previewMode: previewMode}">
    <Topbar class="topbar" v-on:preview="preview"/>
    <main>
      <Editor v-bind:resume="resume" class="editor"/>
      <Preview v-bind:resume="resume" class="preview"/>
    </main>
    <el-button id="exitpreview" v-on:click="exitpreview">退出预览</el-button>
  </div>
</template>

<script>
import Topbar from './components/Topbar'
import Editor from './components/Editor'
import Preview from './components/Preview'

export default {
  data(){
    return{
      previewMode: false,
      resume:{
        profile:[ {name: '',age: '',city: '',birth: ''} ],
        workHistory:[ {company: '',duration: '',content: '',} ],
        studyHistory:[ {school: '',time: '',major: '',degree: ''} ],
        projects:[ {name: '',content: ''} ],
        awards:[ {name: ''} ],
        contacts:[ {qq: '',wechat: '',emali: '',phone: ''} ]
      }
    }
  },
  methods:{
    preview(){
      this.previewMode = true
    },
    exitpreview(){
      this.previewMode = false
    }
  },
  name: 'app',
  components: {
    Topbar,Editor,Preview
  }
}
</script>

<style lang="scss">
html,body,#app{
  height: 100%;
  overflow: hidden;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  height: 100vh;
  flex-direction: column;
}
.topbar{
  position: relative;
  z-index: 1;
  box-shadow: 0 0 3px hsla(0,0,0,0.5);
}
.icon {
       width: 1em; height: 1em;
       vertical-align: -0.15em;
       fill: currentColor;
       overflow: hidden;
}
#app main{
  display: flex;
  flex: 1;
  background: #ddd;
  > .editor{
    background: #fff;
    width: 40em;
    margin: 16px 8px 16px 16px;
    box-shadow: 0 0 3px hsla(0,0,0,0.5);
    border-radius: 4px;
    overflow: auto;
  }
  > .preview{
    background: #fff;
    flex: 1;
    margin: 16px 16px 16px 8px;
    box-shadow: 0 0 3px hsla(0,0,0,0.5);
    border-radius: 4px;
    overflow: hidden;
  }
}
.previewMode > #topbar{
  display: none;
}
.previewMode #editor{
  display: none;
}
.previewMode #preview{
  max-width: 800px;
  margin: 32px auto;
}
#exitpreview{
  display: none;
}
.previewMode #exitpreview{
  display: inline-block;
  position: fixed;
  right: 16px;
  bottom: 16px;
}
</style>
