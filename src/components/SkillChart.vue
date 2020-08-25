<script>
import { HorizontalBar } from 'vue-chartjs'

export default {
    extends: HorizontalBar,
    props: ['data'],
    data() {
        return {
            chartdata: {},
            options: {}
        }
    },
    mounted () {
        this.buildChart();
    },
    methods: {
        buildChart() {
            this.chartdata = {
                labels: this.data.labels,
                datasets: [{
                    backgroundColor: this.data.colors,
                    data: this.data.values,
                    borderWidth: 1
                }]
            };
            this.options = {
                responsive: true,
                maintainAspectRatio: false,
                tooltips: {
                    enabled: false
                },
                scales: {
                    yAxes: [
                    {
                        gridLines: {
                            display: false
                        },
                        ticks: {
                            beginAtZero: true
                        },
                    }],
                    xAxes: [
                    {
                        gridLines: {
                            lineWidth: 0,
                            zeroLineColor: "#111",
                            zeroLineWidth: 1
                        },
                        ticks: {
                            display: false,
                            beginAtZero: true
                        }
                    }]
                },
                legend: {
                    display: false
                },
                animation: {
                    duration: 1000,
                    easing: 'easeInOutSine'
                }
            }
            this.renderChart(this.chartdata, this.options)
        },
    },
    watch: {
        data: function() {
            this.buildChart();
        }
    }
}
</script>

<style>
</style>
