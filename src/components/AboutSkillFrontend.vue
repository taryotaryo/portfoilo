<script>
import { Bar } from 'vue-chartjs'
export default {
  extends: Bar,
  data: function () {
    return {
      type: 'bar',
      data: {
        labels: ['HTML', 'CSS', 'SCSS', 'Bootstrap', 'JavaScript', 'jQuery', 'Vue.js'],
        datasets: [
          {
            data: [80, 70, 80, 40, 60, 50, 70, 80, ''],
            backgroundColor: [
              '#fff',
              '#fff',
              '#fff',
              '#fff',
              '#fff',
              '#fff',
              '#fff'
            ],
            barPercentage: 0.2
          }
        ]
      },
      options: {
        responsive: false,
        legend: {
          display: false
        },
        scales: {
          xAxes: [{
            display: true,
            position: 'top',
            ticks: {
              min: 0,
              max: 100,
              fontSize: 14,
              fontColor: '#fff'
            }
          }],
          yAxes: [{
            display: false
          }]
        }
      }
    }
  },
  mounted () {
    this.renderChart(this.data, this.options)
  }
}
</script>
