<template>
  <div class="lang_wrapper">
    <label for="lang_select" class="label">Language</label>
    <select name="lang_select" id="lang_select" class="select_list" @change="chooseLanguage($event)">
      <option v-for="option in langs" :selected="currentLanguage == option" :value="option" :key="langs.indexOf(option)">{{ option }}</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "Select",
  props: {
    curLang: Function,
    langsArray: Array,
    langsFunc: Function
  },
  data() {
    return {
      langs: this.langsArray,
      chooseLanguage: this.langsFunc,
      currentLanguage: this.curLang
    }
  },
}
</script>

<style scoped>
.lang_wrapper {
  max-width: 220px;
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
}
.label {
  font-size: 16px;
  font-weight: 500;
  line-height: 1.2;
  text-align: left;
  margin: 0px 8px 0px 0px;
  color: #242424;
}
.select_list {
  width: 100%;
  height: 28px;
  outline: none;
  cursor: pointer;
}
</style>