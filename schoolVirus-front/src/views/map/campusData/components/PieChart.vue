<template>
    <div :class="className" :style="{ height: height, width: width }" />
</template>

<script>
import echarts from "echarts";
require("echarts/theme/macarons"); // echarts theme
import resize from "./mixins/resize";

export default {
    mixins: [resize],
    props: {
        className: {
            type: String,
            default: "chart",
        },
        width: {
            type: String,
            default: "100%",
        },
        height: {
            type: String,
            default: "300px",
        },
    },
    data() {
        return {
            chart: null,
        };
    },
    mounted() {
        this.$nextTick(() => {
            this.initChart();
        });
    },
    beforeDestroy() {
        if (!this.chart) {
            return;
        }
        this.chart.dispose();
        this.chart = null;
    },
    methods: {
        initChart() {
            this.chart = echarts.init(this.$el, "macarons");

            this.chart.setOption({
                tooltip: {
                    trigger: "item",
                    formatter: "{a} <br/>{b} : {c} ({d}%)",
                },
                
                legend: {
                    left: "center",
                    bottom: "10",
                    data: [
                        "Diagnosis Management",
                         "close contact",
                         "Medium to high risk",
                         "lower risk"
                    ]
                },
                series: [
                    {
                        name: "On-campus epidemic data",
                        type: "pie",
                        roseType: "radius",
                        radius: [15, 95],
                        center: ["50%", "38%"],
                        data: [
                            { value: 320, name: "Diagnosis management" },
                            { value: 240, name: "close contact" },
                            { value: 149, name: "Medium to high risk" },
                            { value: 59, name: "lower risk" },
                        ],
                        animationEasing: "cubicInOut",
                        animationDuration: 2600,
                    },
                ],
            });
        },
    },
};
</script>
