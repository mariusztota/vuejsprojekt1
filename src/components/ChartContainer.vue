<script>
import { Line } from 'vue-chartjs';

export default {
  extends: Line,
  props: {
    currencyData: {
      type: Array,
      default: null,
    },
  },
  mounted() {
    let currency = this.currencyData;

    let labels = [];
    let dataVals = [];
    currency.forEach((element) => {
      labels.push(element.effectiveDate);
      dataVals.push(element.mid);
    });

    let chartData = {
      labels: labels,
      datasets: [
        {
          label: 'Wartość (PLN)',
          data: dataVals,
          borderWidth: 1,
          backgroundColor: ['rgba(255, 99, 132, 0.2)'],
          borderColor: ['rgba(255,99,150,1)'],
        },
      ],
    };
    this.renderChart(chartData, {
      elements: {
        line: {
          tension: 0,
        },
      },

      responsive: true,
    });
  },
};
</script>
