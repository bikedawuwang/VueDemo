<template>
    <div id="myChart"  ref="myChart":style="{width: '300px', height: '300px'}"></div>
</template>

<script>
export default {
    name: 'Echarts',
    props: ['theme'],
    data () {
        return {
            option: {
                tooltip: {
                    trigger: 'item',
                    formatter: '{a} <br/>{b}: {c} ({d}%)'
                },
                legend: {
                    orient: 'vertical',
                    left: 10,
                    data: ['直接访问', '邮件营销', '联盟广告', '视频广告', '搜索引擎']
                },
                series: [
                    {
                        name: '访问来源',
                        type: 'pie',
                        avoidLabelOverlap: false,
                        label: {
                            show: false,
                            position: 'center'
                        },
                        emphasis: {
                            label: {
                                show: false,
                                fontSize: '30',
                                fontWeight: 'bold'
                            }
                        },
                        labelLine: {
                            show: false
                        },
                        data: [
                            {value: 335, name: '直接访问'},
                            {value: 310, name: '邮件营销'},
                            {value: 234, name: '联盟广告'},
                            {value: 135, name: '视频广告'},
                            {value: 1548, name: '搜索引擎'}
                        ]
                    }
                ]
            }
        }
    },
    mounted() {
        this.drawLine();
    },
    methods: {
        drawLine(){
            // 基于准备好的dom，初始化echarts实例
            const myCharts = this.$echarts.init(this.$refs.myChart);
            console.log("drawLine -> option", this.option)
            if (this.theme == 'b') {
                this.option.series[0].radius = ['50%', '70%'];
                this.option.series[0].emphasis.label.show = true;
            }
            else {
                this.option.series[0].radius = '70%';
                this.option.series[0].emphasis.label.show = false;
            }
            // 绘制图表s
            myCharts.setOption(this.option);
        }
    },
    watch: {
        theme(nextProps, preProps) {
            if (nextProps !== preProps) {
                this.props = nextProps;
                this.drawLine();
            }
        }
    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
    font-weight: normal;
}
ul {
    list-style-type: none;
    padding: 0;
}
li {
    display: inline-block;
    margin: 0 10px;
}
a {
    color: #42b983;
}
</style>
