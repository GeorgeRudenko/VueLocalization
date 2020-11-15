<script>
import englishLanguage from "@/localizationController/localizations/en.json";
import russianLanguage from "@/localizationController/localizations/ru.json";
import germanyLanguage from "@/localizationController/localizations/de.json";

export default {
  name: "Controller",
  data() {
    return {
      currentLanguage: '',
      defaultLanguage: "ENGLISH",
      langs: ["ENGLISH", "RUSSIAN", "GERMANY"],
      translate: {
        ENGLISH: englishLanguage,
        RUSSIAN: russianLanguage,
        GERMANY: germanyLanguage,
      }
    }
  },
  created() {
    this.currentLanguage = (localStorage.currentLange) ? localStorage.currentLange : this.defaultLanguage;
  },
  methods: {
    getCurrentLang() {
      let res = this.currentLanguage;

      return res ? res : this.defaultLanguage;
    },
    lang(str) {
      let string = str ? str : null;
      let result = '';
    
      switch (this.getCurrentLang()) {
        case ('ENGLISH'):
          result = this.translate.ENGLISH[string]
          break;
        case ('RUSSIAN'):
          result = this.translate.RUSSIAN[string]
          break;
        case ('GERMANY'):
          result = this.translate.GERMANY[string]
          break;
        default:
          console.error("The language array does not contain the selected language!")
          break;
      }
    
      return (result) ? result : console.error("Wrong string key:", string);
    },
    chooseLanguage(e) {
      this.currentLanguage = e.target.value;
      localStorage.currentLange = e.target.value;
    }
  }
}
</script>
