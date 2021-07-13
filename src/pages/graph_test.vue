<template>

    <div class="container">
      <br>
      <br>
      <select v-model="selected">
          <option  value="表示したいグラフを選んでください">Please Select</option>
            <option value="Open">始値(open)</option>
            <option value="Low">安値(low)</option>
            <option value="High">高値(high)</option>
            <option value="Close">終値(close)</option>
      </select>

      <div id="app">

        <p v-if="selected == '表示したいグラフを選んでください'">
          <line-chart
            :data="chartData_open"
            :options="options"
            :height="100"
          ></line-chart>

          <line-chart
            :data="chartData_low"
            :options="options"
            :height="100"
          ></line-chart>

          <line-chart
            :data="chartData_high"
            :options="options"
            :height="100"
          ></line-chart>

          <line-chart
            :data="chartData_close"
            :options="options"
            :height="100"
          ></line-chart>
        </p>

        <p v-else-if="selected == 'Open'">
          <line-chart
            :data="chartData_open"
            :options="options"
            :height="100"
        ></line-chart></p>

        <p v-else-if="selected == 'Low'">
          <line-chart
            :data="chartData_low"
            :options="options"
            :height="100"
        ></line-chart></p>

        <p v-else-if="selected == 'High'">
          <line-chart
            :data="chartData_high"
            :options="options"
            :height="100"
        ></line-chart></p>

        <p v-else-if="selected == 'Close'">
          <line-chart
            :data="chartData_close"
            :options="options"
            :height="100"
        ></line-chart></p>

      {{selected}}
      </div>
    </div>
</template>

<script>
import LineChart from "../timechart.vue";
export default {
  name: "ChartLineSample",
  components: {
    LineChart
  },
  data: 
  function() {
    
    var datas2 = JSON.parse(localStorage.getItem('datalist'));
    //var code_name = localStorage.getItem('code');
    return {
      selected: "表示したいグラフを選んでください",
      datas:JSON.parse(localStorage.getItem('datalist')),


      chartData_open: {
        //x軸
        labels: [datas2.timestamp[235], datas2.timestamp[236], datas2.timestamp[237],datas2.timestamp[238], datas2.timestamp[239], datas2.timestamp[240],datas2.timestamp[241], datas2.timestamp[242], datas2.timestamp[243]],
        // データ詳細
        datasets: [
          {
          //グラフタイトル
            label: datas2.name,
            //データ値(y軸)
            data: [datas2.open[235], datas2.open[236], datas2.open[237],datas2.open[238], datas2.open[239], datas2.open[240],datas2.open[241], datas2.open[242], datas2.open[243]],
            backgroundColor: "#6090EF",
          }
        ]
      },
      chartData_close: {
        //x軸
        labels: [datas2.timestamp[235], datas2.timestamp[236], datas2.timestamp[237],datas2.timestamp[238], datas2.timestamp[239], datas2.timestamp[240],datas2.timestamp[241], datas2.timestamp[242], datas2.timestamp[243]],
        // データ詳細
        datasets: [
          {
          //グラフタイトル
            label: datas2.name,
            //データ値(y軸)
            data: [datas2.close[235], datas2.close[236], datas2.close[237],datas2.close[238], datas2.close[239], datas2.close[240],datas2.close[241], datas2.close[242], datas2.close[243]],
            backgroundColor:"#98fb98",
          }
        ]
      },
      chartData_low: {
        //x軸
        labels: [datas2.timestamp[235], datas2.timestamp[236], datas2.timestamp[237],datas2.timestamp[238], datas2.timestamp[239], datas2.timestamp[240],datas2.timestamp[241], datas2.timestamp[242], datas2.timestamp[243]],
        // データ詳細
        datasets: [
          {
          //グラフタイトル
            label: datas2.name,
            //データ値(y軸)
            data: [datas2.low[235], datas2.low[236], datas2.low[237],datas2.low[238], datas2.low[239], datas2.low[240],datas2.low[241], datas2.low[242], datas2.low[243]],
          }
        ]
      },
      chartData_high: {
        //x軸
        labels: [datas2.timestamp[235], datas2.timestamp[236], datas2.timestamp[237],datas2.timestamp[238], datas2.timestamp[239], datas2.timestamp[240],datas2.timestamp[241], datas2.timestamp[242], datas2.timestamp[243]],
        // データ詳細
        datasets: [
          {
          //グラフタイトル
            label: datas2.name,
            //データ値(y軸)
            data: [datas2.high[235], datas2.high[236], datas2.high[237],datas2.high[238], datas2.high[239], datas2.high[240],datas2.high[241], datas2.high[242], datas2.high[243]],
          }
        ]
      },
      options: {responsive: true
                      , maintainAspectRatio: true
                      , animation: false},
      addFlag: false,

    };
  },
};
</script>

<style>
.input-group {
  margin: 5px;
}
</style>