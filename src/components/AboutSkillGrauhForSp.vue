<script>
import { HorizontalBar } from 'vue-chartjs'
export default {
  extends: HorizontalBar,
  data: function () {
    return {
      type: 'horizontalBar',
      data: {
        labels: ['HTML', 'CSS', 'SCSS', 'Bootstrap', 'JavaScript', 'jQuery', 'Vue.js', 'PHP', 'Ruby', 'rails', 'SQL', 'WordPress', 'Firebase', 'Github'],
        datasets: [
          {
            data: [80, 60, 70, 40, 60, 60, 70, 80, 30, 40, 40, 50, 70, 60, 70, 80],
            backgroundColor: [
              '#fff',
              '#fff',
              '#fff',
              '#fff',
              '#fff',
              '#fff',
              '#fff',
              '#8e8e8e',
              '#8e8e8e',
              '#8e8e8e',
              '#8e8e8e',
              '#8e8e8e',
              '#8e8e8e',
              '#8e8e8e'
            ],
            barPercentage: 0.4
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
            display: false,
            ticks: {
              min: 0,
              max: 100,
              fontSize: 14,
              fontColor: '#fff'
            }
          }],
          yAxes: [{
            display: true,
            ticks: {
              min: 0,
              max: 100,
              fontSize: 14,
              fontColor: '#fff'
            }
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
