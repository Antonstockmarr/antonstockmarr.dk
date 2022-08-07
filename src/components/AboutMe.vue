<template>
    <div class="about-me">
        <Wrapper :width="'1000px'">
            <h1 :class="{hiddenLeft: !show}" class="about-me">About me</h1>
            <div class="grid">
                <div class="info-box" :class="{hiddenLeft: !show}">
                    <img src="@/assets/me.jpg" alt="">
                </div>
                <div class="description" :class="{hiddenRight: !show}">
                    <p>
                        I am a newly graduated software engineer from Technical University of Denmark. I love to spend way too much time learning about new technologies and acquiring new skills.
                        This curiosity has brought me wide and far. During my studies I have worked with everything from numerical optimization and high-performance computing to cloud-native software development.
                        My latest interest is accessibility in web development. The internet should be for everyone, and this is a cause I will bring to future projects.
                    </p>
                    <div class="description-fade"></div>
                </div>
            </div>
        </Wrapper>
    </div>
</template>



<script>
import Wrapper from "./Wrapper"

export default {
    name: 'AboutMe',
    components: {
    Wrapper,
},
    data() {
        return {
            show: false,
            render: false
        }
    },
    props: ["toggle"],
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

.about-me {
    background-color: var(--col2);
    padding-bottom: 25px;
}

.info-box, .description {
    padding: 25px 15px;
}

img {
    width: 80%;
    display: block;
    margin: 0px auto 0;
}

h1 {
    font-size: 32px;
    text-align: center;
    line-height: 50px;
    text-transform: uppercase;
}

.description {
    box-sizing: border-box;
    width: 100%;
    text-align: center;
    font-size: 24px;
    line-height: 30px;
}

.skills-container {
    padding: 25px 15px;
}

@media only screen and (min-width: 1000px) {

    .about-me {
        overflow: hidden;
    }

    img {
        width: 400px;
    }

    .grid {
        display: -ms-grid;
        display: grid;
        -ms-grid-columns: 1fr 2fr;
        grid-template-columns: 1fr 2fr;
        box-sizing: border-box;
    }

    .description {
        position: relative;
        background-color: var(--col1);
        padding: 25px;
        width: calc(100% - 30px);
        margin: 25px 15px;
    }

    .description-fade {
        display: block;
        position: absolute;
        height: 100%;
        width: 200px;
        top: 0;
        right: -200px;
        background: linear-gradient(to right, var(--col1) 0%, var(--col2) 100%);
    }

    .description p {
        position: relative;
        top: 50%;
        -webkit-transform: translateY(-50%);
        -ms-transform: translateY(-50%);
        transform: translateY(-50%);
    }

    .grid div, .about-me {
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