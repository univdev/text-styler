<template>
  <text-generator-template
    v-model:text="payload.text"
    v-model:font-size="payload.fontSize"
    v-model:background-color="payload.backgroundColor"
    v-model:color="payload.color"
    v-model:italic="payload.isItalic"
    v-model:bold="payload.isBold"
    v-model:underline="payload.isUnderline"
    @click:github-button="onClickGithub"
    @save="onSave"
    @reset="onResetPayload"
  />
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';
import TextGeneratorTemplate from '@/components/templates/TextGenerator.vue';

export default defineComponent({
  name: 'IndexPage',
  components: {
    TextGeneratorTemplate,
  },
  setup() {
    const download = (uri: string) => {
      const link = document.createElement('a');
      link.download = '이미지.png';
      link.href = uri;
      link.click();
      link.remove();
    };
    const onSave = (uri: string) => {
      download(uri);
    };
    const payload = reactive({
      backgroundColor: '#FFF' as string,
      color: '#000' as string,
      text: '텍스트' as string,
      fontSize: 14 as number,
      isBold: false as boolean,
      isItalic: false as boolean,
      isUnderline: false as boolean,
    });
    const onClickGithub = () => {
      window.open(import.meta.env.VITE_GITHUB_REPOSITORY_URI);
    };
    const onResetPayload = () => {
      payload.backgroundColor = '#FFF';
      payload.color = '#000';
      payload.text = '텍스트';
      payload.fontSize = 14;
      payload.isBold = false;
      payload.isItalic = false;
      payload.isUnderline = false;
    };
    return {
      payload,
      onClickGithub,
      onResetPayload,
      onSave,
    };
  },
});
</script>
