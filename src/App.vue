<template>
  <div class="project-wrapper">
    <!-- Language Example -->
    <h2 class="title">{{ lang("project.title.greeting") }}</h2>
    <!-- Language select list -->
    <LangSelect :langsArray="langs" :curLang="getCurrentLang()" :langsFunc="chooseLanguage"></LangSelect>
  </div>
</template>

<script>
import languageController from '@/localizationController/LangController'
import languageSelect from '@/localizationController/LangSelect'

export default {
  name: 'App',
  mixins: [languageController],
  components: {
    LangSelect: languageSelect,
  },
  methods: {
    checkData(value) {
      if (typeof(value) === 'boolean') {
        return (value != '' && value != null) ? '✔' : '❌';
      }
      else {
        return (value != '' && value != null) ? value : '-';
      }
    },
  }
}
</script>

<style scoped>
.project-wrapper {
  width: 100%;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>