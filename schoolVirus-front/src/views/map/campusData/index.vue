<template>
    <div class="dashboard-editor-container">
       
        <panel-group @handleSetLineChartData="handleSetLineChartData"/>

       
        <el-row class="bigCharts">
           
            <line-chart :chart-data="lineChartData" />
        </el-row>

       
        <el-row :gutter="32">
            <el-col :xs="24" :sm="12" :lg="12">
                <div class="chart-wrapper">
                    <pie-chart />
                </div>
            </el-col>
            <el-col :xs="24" :sm="12" :lg="12">
                <div class="chart-wrapper">
                    <bar-chart />
                </div>
            </el-col>
        </el-row>
    </div>
</template>

<script>
import PanelGroup from "./components/PanelGroup";
import LineChart from "./components/LineChart";
import PieChart from "./components/PieChart";
import BarChart from "./components/BarChart";

// Data panel custom data
const lineChartData = {
    // Tier 1 (actual and expected data from Monday to Friday)
    newVisitis: {
        expectedData: [100, 120, 161, 134, 105, 160, 165],
        actualData: [120, 82, 91, 154, 162, 140, 145],
    },
    // Tier 2 (actual and expected data from Monday to Friday)
    messages: {
        expectedData: [200, 192, 120, 144, 160, 130, 140],
        actualData: [180, 160, 151, 106, 145, 150, 130],
    },
    // Tier 3 (actual and expected data from Monday to Friday)
    purchases: {
        expectedData: [80, 100, 121, 104, 105, 90, 100],
        actualData: [120, 90, 100, 138, 142, 130, 130],
    },
    // Tier 4 (actual and expected data from Monday to Friday)
    shoppings: {
        expectedData: [130, 140, 141, 142, 145, 150, 160],
        actualData: [120, 82, 91, 154, 162, 140, 130],
    },
};

export default {
    name: "CampusData",
    components: {
        PanelGroup,
        LineChart,
        PieChart,
        BarChart,
    },
    data() {
        return {
            
            lineChartData: lineChartData['newVisitis']
        };
    },
    methods: {
       
        handleSetLineChartData(type) {
            this.lineChartData = lineChartData[type];
        },
    },
};
</script>

<style lang="scss" scoped>
.dashboard-editor-container {
    padding: 20px;
    position: relative;
    background-color:#f0f2f5;
    .bigCharts {
        background: white;
        padding: 16px 16px 0;
        margin-bottom: 32px;
    }
    .chart-wrapper {
        background: #fff;
        padding: 16px 16px 0;
        margin-bottom: 32px;
    }
}

@media (max-width: 1024px) {
    .chart-wrapper {
        padding: 8px;
    }
}
</style>
