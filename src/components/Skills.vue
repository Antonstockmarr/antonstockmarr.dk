<template>
  <div class="skills">
      <div class="chart-container">
        <SkillChart class="chart" :data="chartData"/>
      </div>
  </div>
</template>



<script>
import SkillChart from "./SkillChart"

export default {
    name: 'Skills',
    components: {SkillChart},
    props: ["toggle"],
    computed: {
        chartData() {
            return {
                labels: ['Algorithms','Java/OOP', 'Databases', 'Operations Research', 'Data Analysis', 'html/css', 'JavaScript', 'Vue'],
                values: this.toggle ? ['8','7','6','5','4','3','3','3'] : '0',
                colors: ['#9242E6','#FF6F66','#668BFF','#8AFFE1', '#FA7DE5','#E64B4B','#FAF563','#44E360']
            }
        },
    }
}
</script>

<style scoped>

.skills {
    padding: 20px 15px 40px;
}

.chart-container {
    position: relative;
    box-sizing: border-box;
    width: 100%;
    height: 400px;
}

.chart {
    width: 100%;
    height: 100%;
}


</style>
