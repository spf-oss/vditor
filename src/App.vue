<template>
  <div id="editor"></div>
  <button @click="setValue">按钮</button>
  <button @click="getHtml">获取html</button>
  <button @click="setTheme1">获取html</button>
  <button @click="setTheme2">获取html</button>
</template>

<script lang="ts">
import { defineComponent, ref, onMounted} from 'vue';
import Vditor from 'vditor'
import 'vditor/dist/index.css'

var refEditor = ref<Vditor>();

export default defineComponent({
  name: 'App',
  setup() {
    const setValue = ()=>{
      refEditor.value?.insertValue("我仙子啊")
    }

    const getHtml = ()=>{
      console.log(refEditor.value?.getHTML())
    }

    const setTheme1 = ()=>{
      refEditor.value?.setTheme("classic")
    }
    const setTheme2 = ()=>{
      refEditor.value?.setTheme("dark")
    }

    onMounted(() => {
      refEditor.value = new Vditor("editor", {
        height: 720,
      });
    })

    return {
      refEditor,
      setValue,
      getHtml,
      setTheme1,
      setTheme2
    }
  },
});
</script>
