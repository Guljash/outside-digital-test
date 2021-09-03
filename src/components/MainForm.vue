<template>
  <form class="main-form" @submit.prevent="$emit('count', input)">
    <ul>
      <li><label for="input">Ваша зарплата в месяц</label></li>
      <li>
        <input
          v-model="input"
          name="input"
          type="number"
          placeholder="Введите данные"
        />
      </li>
      <li><button>Рассчитать</button></li>
    </ul>
  </form>
</template>

<script>
export default {
    data() {
        return {
            input: ""
        }
    }
}
</script>