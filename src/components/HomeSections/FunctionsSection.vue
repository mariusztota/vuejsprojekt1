<template>
  <section class="page-section bg-primary text-white mb-0" id="funkcje">
    <div class="container">
      <div id="app">
        <!-- Sekcja Funkcje Tytuł-->
        <h2 class="page-section-heading text-center text-uppercase text-white">Funkcje</h2>
        <!-- Podział Ikon-->
        <div class="divider-custom divider-light">
          <div class="divider-custom-line"></div>
          <div class="divider-custom-icon"><i class="fas fa-star"></i></div>
          <div class="divider-custom-line"></div>
        </div>
      </div>
      <!-- Funkcjonalności-->
      <!-- Kursy walut-->
      <div class="col-md-12 text-center">
        <button
          class="btn btn-light"
          type="button"
          data-toggle="collapse"
          data-target="#collapseTable "
          aria-expanded="false"
          aria-controls="collapseTable"
        >
          Aktualne Kursy Walut
        </button>
        <div class="mt-4 collapse" id="collapseTable">
          <div class="card card-body content-container">
            <CurrencyExchange />
          </div>
        </div>
      </div>
      <br />
      <!-- Wykres-->
      <div class="col-md-12 text-center">
        <button
          class="btn btn-light"
          type="button"
          data-toggle="collapse"
          data-target="#collapseConverter "
          aria-expanded="false"
          aria-controls="collapseConverter"
        >
          Przykładowe Funkcje
        </button>
        <div class="mt-4 collapse" id="collapseConverter">
          <div class="card card-body content-container">
            <CurrencyCalculator />
          </div>
        </div>
      </div>
      <br />
      <!-- Kursy walut FUNT SZTERLING-->
      <div class="col-md-12 text-center">
        <button
          class="btn btn-light"
          type="button"
          data-toggle="collapse"
          data-target="#collapseChart1"
          aria-expanded="false"
          aria-controls="collapseChart1"
        >
          Wykres- Funt Szterling
        </button>
        <div class="mt-4 collapse" id="collapseChart1">
          <div class="card card-body content-container">
            <ChartContainer v-if="this.gbpDataSeries !== null" :currencyData="this.gbpDataSeries" />
          </div>
        </div>

        <!-- Kursy walut EURO-->
        <br />
        <br />
        <button
          class="btn btn-light"
          type="button"
          data-toggle="collapse"
          data-target="#collapseChart2"
          aria-expanded="false"
          aria-controls="collapseChart2"
        >
          Wykres- Euro
        </button>
        <div class="mt-4 collapse" id="collapseChart2">
          <div class="card card-body content-container">
            <ChartContainer v-if="this.eurDataSeries !== null" :currencyData="this.eurDataSeries" />
          </div>
        </div>
      </div>
      <br />
    </div>
  </section>
</template>

<script>
import axios from 'axios';
import ChartContainer from '../../components/ChartContainer';
import CurrencyExchange from '../../components/CurrencyExchange.vue';
import CurrencyCalculator from '../../components/CurrencyCalculator.vue';
export default {
  name: 'FunctionSection',
  components: { CurrencyExchange, ChartContainer, CurrencyCalculator },
  data: function() {
    return {
      gbpDataSeries: null,
      eurDataSeries: null,
      loadedGbp: false,
      loadedEur: false,
    };
  },
  async mounted() {
    this.loadedGbp = false;
    this.loadedEur = false;
    // Kurs Funta szterlinga (10 dni)
    axios
      .get('https://api.nbp.pl/api/exchangerates/rates/a/gbp/last/10/?format=json')
      .then((response) => {
        this.gbpDataSeries = response.data.rates;
      })
      .catch((error) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => {
        this.loadedGbp = true;
      });

    //  kurs Euro
    axios
      .get('https://api.nbp.pl/api/exchangerates/rates/a/eur/last/10/?format=json')
      .then((response) => {
        this.eurDataSeries = response.data.rates;
      })
      .catch((error) => {
        console.log(error);
        this.errored = true;
      })
      .finally(() => (this.loadedEur = true));
  },
};
</script>
