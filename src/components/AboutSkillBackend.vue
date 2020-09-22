<script>
import { Bar } from 'vue-chartjs'
export default {
  extends: Bar,
  data: function () {
    return {
      type: 'bar',
      data: {
        labels: ['PHP', 'Ruby', 'rails', 'SQL', 'WordPress', 'Netlify', 'Github'],
        datasets: [
          {
            data: [-30, -40, -40, -50, -60, -50, -80, ''],
            backgroundColor: [
              '#8e8e8e',
              '#8e8e8e',
              '#8e8e8e',
              '#8e8e8e',
              '#8e8e8e',
              '#8e8e8e',
              '#8e8e8e'
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
            position: 'bottom',
            ticks: {
              min: -100,
              max: 0,
              fontSize: 14,
              fontColor: '#8e8e8e'
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
