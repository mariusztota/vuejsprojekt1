<template>
  <div id="app">
    <div id="getStarted">
      <button type="button" v-on:click="getTested()">Start</button>
    </div>
    <div id="mainApp" style="display: none">
      <table>
        <tr>
          <td><button type="button" v-on:click="countAvgUSD()">Average USD value</button></td>
          <td id="avgUSD"></td>
        </tr>
        <tr>
          <td><button type="button" v-on:click="countAvgEUR()">Average EUR value</button></td>
          <td id="avgEUR"></td>
        </tr>
        <tr>
          <td><button type="button" v-on:click="countAvgCHF()">Average CHF value</button></td>
          <td id="avgCHF"></td>
        </tr>
        <tr>
          <td><button type="button" v-on:click="countAvgNOK()">Average NOK value</button></td>
          <td id="avgNOK"></td>
        </tr>
      </table>

      <button type="button" v-on:click="showConverter()">Currency Converter</button>
      <div id="myConverter" style="display: none">
        <a>Wprowadź kwotę</a><br />
        <input type="number" id="valueAmount" /><br />
        <a>wybierz walutę</a><br />
        <select id="convertSelection">
          <option value="0"></option>
          <option value="USD">USD</option>
          <option value="EUR">EUR</option>
          <option value="CHF">CHF</option>
          <option value="NOK">NOK</option>
        </select>
        <a>Wybierz datę między 1 stycznia 2020 a 31 grudnia 2020</a><br />
        <input type="date" min="2020-01-01" max="2020-12-31" id="convertDateInput" />
        <button type="button" v-on:click="CalculateValue()">printValues</button><br />
        <a id="convertResult">Tutaj pojawi się wynik</a>
      </div>
      <button type="button" v-on:click="minMaxHide()">Min / Max</button>
      <div id="minmax" style="display: none">
        <p>Jakiej wartości oczekujesz:</p>
        <div>
          <input type="radio" id="maxVal" name="extremum" value="max" />
          <label for="max">Maksymalnej</label><br />
          <input type="radio" id="minVal" name="extremum" value="min" />
          <label for="min">Minimalnej</label><br />
          <a>Wybierz walutę</a>
          <select id="selectMinMax">
            <option value="0"></option>
            <option value="USD">USD</option>
            <option value="EUR">EUR</option>
            <option value="CHF">CHF</option>
            <option value="NOK">NOK</option></select
          ><br />
          <input type="date" min="2020-01-01" max="2020-12-31" id="startDate" /><br />
          <input type="date" min="2020-01-01" max="2020-12-31" id="endDate" /><br />
        </div>
        <button type="button" v-on:click="minMax()">Jedziemy!</button><br />
        <a id="minmaxresult"></a><br />
      </div>
      <div>
        <a>Kursy</a>
        <table>
          <tr>
            <th>Data</th>
            <th>USD</th>
            <th>EUR</th>
            <th>CHF</th>
            <th>NOK</th>
          </tr>
          <tr v-for="(item, index) in allData" :key="item.date">
            <td>{{ item.a }}</td>
            <td>{{ item.usdVal }}</td>
            <td>{{ item.eurVal }}</td>
            <td>{{ item.chfVal }}</td>
            <td>{{ item.nokVal }}</td>
          </tr>
        </table>
      </div>
    </div>
  </div></template
>

<script>
import axios from 'axios';
import moment from 'moment';

export default {
  name: 'CurrencyCalculator',
  components: {},
  data: function() {
    return {
      currDataUSD: null,
      currDataEUR: null,
      currDataCHF: null,
      currDataNOK: null,
      allData: [],
      minmax: [],
    };
  },
  mounted: function() {
    axios.get('https://my.api.mockaroo.com/usddat.json?key=48a0ba60').then((response) => (this.currDataUSD = response.data));
    axios.get('https://my.api.mockaroo.com/euval.json?key=48a0ba60').then((response) => (this.currDataEUR = response.data));
    axios.get('https://my.api.mockaroo.com/chfval.json?key=48a0ba60').then((response) => (this.currDataCHF = response.data));
    axios.get('https://my.api.mockaroo.com/nokval.json?key=48a0ba60').then((response) => (this.currDataNOK = response.data));
  },
  methods: {
    getTested: function() {
      var x = document.getElementById('mainApp');
      var y = document.getElementById('getStarted');
      x.style.display = 'block';
      y.style.display = 'none';
      for (var i = 0; i < this.currDataUSD.length; i++) {
        var usdVal = this.currDataUSD[i].value / 10000;
        var a = this.currDataUSD[i].date;
        for (var j = 0; j < this.currDataEUR.length; j++) {
          var b = this.currDataEUR[j].date;
          if (b === a) {
            var eurVal = this.currDataEUR[j].value / 10000;
            for (var k = 0; k < this.currDataCHF.length; k++) {
              var c = this.currDataCHF[k].date;
              if (c === a) {
                var chfVal = this.currDataCHF[k].value / 10000;
                for (var l = 0; l < this.currDataNOK.length; l++) {
                  var d = this.currDataNOK[l].date;
                  if (d === a) {
                    var nokVal = this.currDataNOK[l].value / 10000;
                    this.allData.push({ a, usdVal, eurVal, chfVal, nokVal });
                    break;
                  }
                }
                break;
              }
            }
            break;
          }
        }
      }

      var myDate = new Date(2020, 0, 1);
      for (var i = 0; i < this.currDataUSD.length; i++) {
        this.currDataUSD[i].date = moment(this.addDays(myDate, i)).format('L');
      }
      for (var i = 0; i < this.currDataEUR.length; i++) {
        this.currDataEUR[i].date = moment(this.addDays(myDate, i)).format('L');
      }
      for (var i = 0; i < this.currDataCHF.length; i++) {
        this.currDataCHF[i].date = moment(this.addDays(myDate, i)).format('L');
      }
      for (var i = 0; i < this.currDataNOK.length; i++) {
        this.currDataNOK[i].date = moment(this.addDays(myDate, i)).format('L');
      }
      for (var i = 0; i < this.allData.length; i++) {
        this.allData[i].a = moment(this.addDays(myDate, i)).format('L');
      }
      console.log(this.allData);
    },

    minMaxHide: function() {
      var x = document.getElementById('minmax');
      if (x.style.display === 'none') {
        x.style.display = 'block';
      } else {
        x.style.display = 'none';
        document.getElementById('maxVal').checked = false;
        document.getElementById('minVal').checked = false;
        document.getElementById('selectMinMax').value = '0';
        document.getElementById('startDate').value = '';
        document.getElementById('endDate').value = '';
        document.getElementById('minmaxresult').innerHTML = '';
      }
    },

    minMax: function() {
      var wantMax = document.getElementById('maxVal').checked;
      var wantMin = document.getElementById('minVal').checked;
      var cur = document.getElementById('selectMinMax').value;
      var startDate = moment(document.getElementById('startDate').value).format('L');
      var endDate = moment(document.getElementById('endDate').value).format('L');
      var errorMsg = '';
      if (wantMax === wantMin) {
        errorMsg = errorMsg + 'Wybierz jedną z opcji!\n';
      }
      if (cur === '0') {
        errorMsg = errorMsg + 'Wybierz walutę!\n';
      }
      if (startDate === 'Invalid date' || endDate === 'Invalid date') {
        errorMsg = errorMsg + 'Wybierz datę początku i końca okresu!\n';
      }
      if (errorMsg.length === 0) {
        var startDay = startDate.split('/')[1];
        var startMonth = startDate.split('/')[0] * 100;
        var startCount = parseFloat(startDay) + parseFloat(startMonth);
        var endDay = endDate.split('/')[1];
        var endMonth = endDate.split('/')[0] * 100;
        var endCount = parseFloat(endDay) + parseFloat(endMonth);
        var minMaxval = 0;
        if (endCount < startCount) {
          alert('Data zakończenia okresu nie może być wcześniejsza niż ropoczęcia!');
        } else {
          switch (cur) {
            case 'USD':
              if (wantMin) {
                minMaxval = parseFloat(this.currDataUSD[0].value);
              }
              for (var i = 0; i < this.currDataUSD.length; i++) {
                var day = this.currDataUSD[i].date.split('/')[1];
                var month = this.currDataUSD[i].date.split('/')[0] * 100;
                var curDateCount = parseFloat(day) + parseFloat(month);
                if (parseFloat(curDateCount) >= parseFloat(startCount) && parseFloat(curDateCount) <= parseFloat(endCount)) {
                  if (wantMin) {
                    if (minMaxval < parseFloat(this.currDataUSD[i].value)) {
                    } else {
                      minMaxval = parseFloat(this.currDataUSD[i].value);
                    }
                  } else {
                    if (minMaxval < parseFloat(this.currDataUSD[i].value)) {
                      minMaxval = parseFloat(this.currDataUSD[i].value);
                    }
                  }
                }
              }
              break;
            case 'EUR':
              if (wantMin) {
                minMaxval = parseFloat(this.currDataEUR[0].value);
              }
              for (var i = 0; i < this.currDataEUR.length; i++) {
                var day = this.currDataEUR[i].date.split('/')[1];
                var month = this.currDataEUR[i].date.split('/')[0] * 100;
                var curDateCount = parseFloat(day) + parseFloat(month);
                if (parseFloat(curDateCount) >= parseFloat(startCount) && parseFloat(curDateCount) <= parseFloat(endCount)) {
                  if (wantMin) {
                    if (minMaxval < parseFloat(this.currDataEUR[i].value)) {
                    } else {
                      minMaxval = parseFloat(this.currDataEUR[i].value);
                    }
                  } else {
                    if (minMaxval < parseFloat(this.currDataEUR[i].value)) {
                      minMaxval = parseFloat(this.currDataEUR[i].value);
                    }
                  }
                }
              }
              break;
            case 'CHF':
              if (wantMin) {
                minMaxval = parseFloat(this.currDataCHF[0].value);
              }
              for (var i = 0; i < this.currDataCHF.length; i++) {
                var day = this.currDataCHF[i].date.split('/')[1];
                var month = this.currDataCHF[i].date.split('/')[0] * 100;
                var curDateCount = parseFloat(day) + parseFloat(month);
                if (parseFloat(curDateCount) >= parseFloat(startCount) && parseFloat(curDateCount) <= parseFloat(endCount)) {
                  if (wantMin) {
                    if (minMaxval < parseFloat(this.currDataCHF[i].value)) {
                    } else {
                      minMaxval = parseFloat(this.currDataCHF[i].value);
                    }
                  } else {
                    if (minMaxval < parseFloat(this.currDataCHF[i].value)) {
                      minMaxval = parseFloat(this.currDataCHF[i].value);
                    }
                  }
                }
              }
              break;
            case 'NOK':
              if (wantMin) {
                minMaxval = parseFloat(this.currDataNOK[0].value);
              }
              for (var i = 0; i < this.currDataNOK.length; i++) {
                var day = this.currDataNOK[i].date.split('/')[1];
                var month = this.currDataNOK[i].date.split('/')[0] * 100;
                var curDateCount = parseFloat(day) + parseFloat(month);
                if (parseFloat(curDateCount) >= parseFloat(startCount) && parseFloat(curDateCount) <= parseFloat(endCount)) {
                  if (wantMin) {
                    if (minMaxval < parseFloat(this.currDataNOK[i].value)) {
                    } else {
                      minMaxval = parseFloat(this.currDataNOK[i].value);
                    }
                  } else {
                    if (minMaxval < parseFloat(this.currDataNOK[i].value)) {
                      minMaxval = parseFloat(this.currDataNOK[i].value);
                    }
                  }
                }
              }
              break;
            default:
              alert('błąd');
          }
          if (wantMin) {
            document.getElementById('minmaxresult').innerHTML = 'Najmniejsza wartość w podanym przedziale to:' + minMaxval / 10000;
          } else {
            document.getElementById('minmaxresult').innerHTML = 'Największa wartość w podanym przedziale to:' + minMaxval / 10000;
          }
        }
      } else {
        alert('Następujące błędy w formularzu: \n' + errorMsg);
      }
    },

    countAvgUSD: function() {
      var itemsAmount = this.currDataUSD.length;
      var total = 0;
      for (var i = 0; i < itemsAmount; i++) {
        total += parseFloat(this.currDataUSD[i].value / 10000);
      }
      document.getElementById('avgUSD').innerHTML = (total / itemsAmount).toFixed(4);
    },

    countAvgEUR: function() {
      var itemsAmount = this.currDataEUR.length;
      var total = 0;
      for (var i = 0; i < itemsAmount; i++) {
        total += parseFloat(this.currDataEUR[i].value / 10000);
      }
      document.getElementById('avgEUR').innerHTML = (total / itemsAmount).toFixed(4);
    },

    countAvgCHF: function() {
      var itemsAmount = this.currDataCHF.length;
      var total = 0;
      for (var i = 0; i < itemsAmount; i++) {
        total += parseFloat(this.currDataCHF[i].value / 10000);
      }
      document.getElementById('avgCHF').innerHTML = (total / itemsAmount).toFixed(4);
    },

    countAvgNOK: function() {
      var itemsAmount = this.currDataNOK.length;
      var total = 0;
      for (var i = 0; i < itemsAmount; i++) {
        total += parseFloat(this.currDataNOK[i].value / 10000);
      }
      document.getElementById('avgNOK').innerHTML = (total / itemsAmount).toFixed(4);
    },

    addDays: function(date, days) {
      var result = new Date(date);
      result.setDate(date.getDate() + days);
      return result;
    },

    showConverter: function() {
      var x = document.getElementById('myConverter');
      if (x.style.display === 'none') {
        x.style.display = 'block';
      } else {
        x.style.display = 'none';
        document.getElementById('valueAmount').value = '';
        document.getElementById('convertSelection').value = '0';
        document.getElementById('convertDateInput').value = '';
        document.getElementById('convertResult').innerHTML = 'Tutaj pojawi się wynik';
      }
    },

    CalculateValue: function() {
      console.log(this.allData);

      var num = document.getElementById('valueAmount').value;
      var cur = document.getElementById('convertSelection').value;
      var dat = moment(document.getElementById('convertDateInput').value).format('L');
      var errorMsg = '';
      if (num === '') {
        errorMsg = errorMsg + 'Podaj poprawną kwotę!\n';
      }
      if (cur === '0') {
        errorMsg = errorMsg + 'Wybierz walutę!\n';
      }
      if (dat === 'Invalid date') {
        errorMsg = errorMsg + 'Wybierz datę między 1 stycznia 2020 a 31 grudnia 2020!';
      }
      if (errorMsg.length === 0) {
        var exrate = 0;
        switch (cur) {
          case 'USD':
            for (var i = 0; i < this.currDataUSD.length; i++) {
              if (this.currDataUSD[i].date === dat) {
                exrate = parseFloat(this.currDataUSD[i].value / 10000);
                break;
              }
            }
            var endValue = (parseFloat(num) / exrate).toFixed(2);
            document.getElementById('convertResult').innerHTML = endValue;
            break;
          case 'EUR':
            for (var i = 0; i < this.currDataEUR.length; i++) {
              if (this.currDataEUR[i].date === dat) {
                exrate = parseFloat(this.currDataEUR[i].value / 10000);
                break;
              }
            }
            var endValue = (parseFloat(num) / exrate).toFixed(2);
            document.getElementById('convertResult').innerHTML = endValue;
            break;
          case 'CHF':
            for (var i = 0; i < this.currDataCHF.length; i++) {
              if (this.currDataCHF[i].date === dat) {
                exrate = parseFloat(this.currDataCHF[i].value / 10000);
                break;
              }
            }
            var endValue = (parseFloat(num) / exrate).toFixed(2);
            document.getElementById('convertResult').innerHTML = endValue;
            break;
          case 'NOK':
            for (var i = 0; i < this.currDataNOK.length; i++) {
              if (this.currDataNOK[i].date === dat) {
                exrate = parseFloat(this.currDataNOK[i].value / 10000);
                break;
              }
            }
            var endValue = (parseFloat(num) / exrate).toFixed(2);
            document.getElementById('convertResult').innerHTML = endValue;
            break;
          default:
            alert('błąd');
        }
      } else {
        alert('Następujące błędy w formularzu: \n' + errorMsg);
      }
    },
  },
};
</script>
