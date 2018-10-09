<template>
  <div id="container" style="width: 100%; height: 400px;"></div>
</template>

<script>
export default{
  mounted(){
    Highcharts.chart('container', {
      chart: {
        type: 'column'
      },
      title: {
        text: 'Fruit Consumption'
      },
      xAxis: {
        categories: ['Apples', 'Bananas', 'Oranges']
      },
      yAxis: {
        title: {
          text: 'Fruit eaten'
        }
      },
      series: [{
        name: 'Stella',
        data: [1,0,4]
      }, {
        name: 'Soo0limm',
        data: [5,7,3]
      }]
    });
  }
}
</script>
