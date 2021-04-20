<template>
  <div v-if="errored">Something went wrong!</div>
  <div v-else>
    <div v-if="loading">Loading...</div>
    <div v-else>
      <table class="table table-dark table-striped table-hover">
        <thead>
          <tr>
            <th scope="col">Waluta</th>
            <th scope="col">Kod</th>
            <th scope="col">Kurs</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item of currency" :key="item.code">
            <td>{{ item.currency }}</td>
            <td>{{ item.code }}</td>
            <td>{{ item.mid }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'CurrencyExchange',
  components: {},
  data() {
    return {
      currency: null,
    };
  },
  mounted() {
    axios
      .get('https://api.nbp.pl/api/exchangerates/tables/a/')
      .then((response) => (this.currency = response.data[0].rates))
      .catch((error) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loading = false));
  },
};
</script>
