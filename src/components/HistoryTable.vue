<template>
  <table>
    <thead>
    <tr>
      <th>#</th>
      <th>Сумма</th>
      <th>Дата</th>
      <th>Категория</th>
      <th>Тип</th>
      <th>Открыть</th>
    </tr>
    </thead>

    <tbody>
    <tr
        v-for="(record, index) in records"
        v-bind:key="record.id"
    >
      <td>{{index + 1}}</td>
      <td>{{record.amount | currencyFilter('RUB')}}</td>
      <td>{{record.date | dateFilter('date')}}</td>
      <td>{{record.categoryName}}</td>
      <td>
        <span class="white-text badge" v-bind:class="[record.typeClass]">{{record.typeText}}</span>
      </td>
      <td>
        <button class="btn-small btn" v-on:click="$router.push('/detail/' + record.id)">
          <i class="material-icons">open_in_new</i>
        </button>
      </td>
    </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  name: 'HistoryTable',
  props: {
    records: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>

</style>
