<template>
  <div class="app">
    <button class="toggle-btn" @click="togglePopUp">Налоговый вычет</button>
  </div>
  <pop-up @closePopUp="togglePopUp" v-if="popUpToggle">
    <h2>Налоговый вычет</h2>
    <p class="tip">
      Используйте налоговый вычет чтобы погасить ипотеку досрочно. Размер
      налогового вычета составляет не более 13% от своего официального годового
      дохода.
    </p>
    <MainForm @count="count"/>
    <ListOfYears :list="list" />
    <div class="select-form">
      <span>Что уменьшаем?</span>
      <button class="btn-active">Платёж</button>
      <button class="btn-disabled">Срок</button>
    </div>
    <button class="add-btn">Добавить</button>
  </pop-up>
</template>

<script>
import PopUp from "./components/PopUp.vue";
import MainForm from "./components/MainForm.vue";
import ListOfYears from "./components/ListOfYears.vue";

export default {
  name: "App",
  components: {
    PopUp, MainForm, ListOfYears
  },
  data() {
    return {
      popUpToggle: false,
      list: [],
    };
  },
  methods: {
    togglePopUp() {
      this.popUpToggle = !this.popUpToggle;
    },
    count(input) {
      this.list = [];
      if (input != "") {
        let tax = input * 0.13 * 12;
        let limit = 260000;
        while (limit > 0) {
          if (limit > tax) {
            this.list.push(tax);
            limit -= tax;
          } else {
            this.list.push(limit);
            limit = 0;
          }
        }
      }
    }
  },
};
</script>
