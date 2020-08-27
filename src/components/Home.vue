<template>
    <div class="home">
        <Wrapper :width="'1000px'">
            <div class="grid">
                <div class="info-box" :class="{hiddenLeft: !show}">
                    <img src="@/assets/me.jpg" alt="">
                    <p>I study Computer Science at Technical University of Denmark, and I have a passion for everything related to software development, from front end to complex algorithms and optimization.</p>
                </div>
                <div class="chart-container" :class="{hiddenRight: !show}">
                    <SkillChart class="chart" :data="chartData"/>
                </div>
            </div>
        </Wrapper>
    </div>
</template>



<script>
import SkillChart from "./SkillChart"
import Wrapper from "./Wrapper"

export default {
    name: 'Home',
    components: {
        SkillChart,
        Wrapper
    },
    data() {
        return {
            show: false,
            render: false
        }
    },
    props: ["toggle"],
    computed: {
        chartData() {
            return {
                labels: ['Algorithms','Java/OOP', 'Databases', 'Operations Research', 'Data Analysis', 'html/css', 'JavaScript', 'Vue'],
                values: this.render ? ['8','7','6','5','4','3','3','3'] : '0',
                colors: ['#9242E6','#FF6F66','#668BFF','#8AFFE1', '#FA7DE5','#E64B4B','#FAF563','#44E360']
            }
        },
    },
    watch: {
        toggle: function(val) {
            if (val === true) {
                this.show = true;
                setTimeout( () => this.render = true, 500);    
            }
        }
    }

}

</script>

<style scoped>
@import "../colors.css";

.home {
    background-color: var(--col2);
}

.info-box, .chart-container {
    padding: 25px 15px;
}

img {
    width: 80%;
    display: block;
    margin: 0px auto 0;
}

p {
    font-size: 16px;
    text-align: center;
    line-height: 20px;
    margin: 10px 0;
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

@media only screen and (min-width: 1000px) {

    .home {
        overflow: hidden;
    }

    img {
        width: auto;
        height: 300px;
    }

 .grid {
        display: -ms-grid;
        display: grid;
        -ms-grid-columns: 1fr 1fr;
        grid-template-columns: 1fr 1fr;
    }

    .grid div {
        -webkit-transition: all 0.5s ease;
        -o-transition: all 0.5s ease;
        transition: all 0.5s ease;
    }

    .hiddenRight {
        opacity: 0;
        -webkit-transform: translateX(200px);
           -moz-transform: translateX(200px);
            -ms-transform: translateX(200px);
                transform: translateX(200px);
    }

    .hiddenLeft {
        opacity: 0;
        -webkit-transform: translateX(-200px);
           -moz-transform: translateX(-200px);
            -ms-transform: translateX(-200px);
                transform: translateX(-200px);
    }
}

</style>