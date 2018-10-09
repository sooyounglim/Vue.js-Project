<template>
  <div id="app">
    <DatePicker></DatePicker>
    <Chart></Chart>
  </div>
</template>

<script>
import DatePicker from './DatePicker.vue'
import Chart from './Chart.vue'

export default{
  name: 'app',
  created(){
    console.log($.fn.jquery);
    console.log($.ui.version);
  },
  components: {
    DatePicker,
    Chart
  }
}
</script>
