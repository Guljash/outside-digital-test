<template>
  <div v-if="list.length > 0" class="computed">
    <span>Итого можете внести в качестве досрочных:</span>
    <ul>
      <li v-for="(el, i) of list" :key="i">
        <div>
          <input type="checkbox" id="checkbox-id" />
          <div class="comp-chbx"><img src="../assets/check.svg" /></div>
          <span>{{ el }} рублей</span>
          <span class="tip"> в {{ ++i }}{{ "-" + ordinalInWord(i) }} год</span>
        </div>
        <hr />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["list"],
  methods: {
    ordinalInWord(cardinal) {
      var ordinals = [
        "ый",
        "ый",
        "ой",
        "ий",
        "ый",
        "ый",
        "ой",
        "ой",
        "ой",
        "ый",
        "ый",
      ];
      if (cardinal <= 20 && cardinal > 10) {
        return ordinals[0];
      } else if (cardinal <= 10 || cardinal % 10 <= 10) {
        return ordinals[cardinal % 10];
      }
    },
  },
};
</script>