<template>
    <el-row :gutter="40" class="panel-group">
        <el-col :xs="24" :sm="12" :lg="6" class="card-panel-col" >
            
            <div
                class="card-panel"
                @click="handleSetLineChartData('newVisitis')"
            >
                <div class="card-panel-icon-wrapper icon-people">
                    <svg-icon
                        icon-class="peoples"
                        class-name="card-panel-icon"
                    />
                </div>
                <div class="card-panel-description">
                    <div class="card-panel-text">Existing diagnosis</div>
                    <count-to
                        :start-val="0"
                        :end-val="num1"
                        :duration="1000"
                        class="card-panel-num"
                    />
                </div>
            </div>
        </el-col>
        <el-col :xs="24" :sm="12" :lg="6" class="card-panel-col">
            <div class="card-panel" @click="handleSetLineChartData('messages')">
                <div class="card-panel-icon-wrapper icon-message">
                    <svg-icon
                        icon-class="message"
                        class-name="card-panel-icon"
                    />
                </div>
                <div class="card-panel-description">
                    <div class="card-panel-text">close contacts</div>
                    <count-to
                        :start-val="0"
                        :end-val="num2"
                        :duration="1000"
                        class="card-panel-num"
                    />
                </div>
            </div>
        </el-col>
        <el-col :xs="24" :sm="12" :lg="6" class="card-panel-col">
            <div
                class="card-panel"
                @click="handleSetLineChartData('purchases')"
            >
                <div class="card-panel-icon-wrapper icon-money">
                    <svg-icon icon-class="money" class-name="card-panel-icon" />
                </div>
                <div class="card-panel-description">
                    <div class="card-panel-text">Moderate to high risk contacts</div>
                    <count-to
                        :start-val="0"
                        :end-val="num3"
                        :duration="1000"
                        class="card-panel-num"
                    />
                </div>
            </div>
        </el-col>
        <el-col :xs="24" :sm="12" :lg="6" class="card-panel-col">
            <div
                class="card-panel"
                @click="handleSetLineChartData('shoppings')"
            >
                <div class="card-panel-icon-wrapper icon-shopping">
                    <svg-icon
                        icon-class="shopping"
                        class-name="card-panel-icon"
                    />
                </div>
                <div class="card-panel-description">
                    <div class="card-panel-text">low risk contacts</div>
                    <count-to
                        :start-val="0"
                        :end-val="num4"
                        :duration="1000"
                        class="card-panel-num"
                    />
                </div>
            </div>
        </el-col>
    </el-row>
</template>

<script>
import CountTo from "vue-count-to";

export default {
    components: {
        CountTo,
    },
    data(){
        return {
            num1:100000,
            num2:100000,
            num3:100000,
            num4:100000,
        }
    },
    methods: {
        handleSetLineChartData(type) {
            console.log(type);
            this.$emit("handleSetLineChartData", type);
        },
    },
};
</script>

<style lang="scss" scoped>

.panel-group {
    margin-top: 18px;

    .card-panel-col {
        margin-bottom: 32px;
    }

    .box_shadow{
        // -webkit-box-shadow: 10px 10px 5px black;
        box-shadow: 0px 0px 8px rgb(104, 104, 104);
    }

    .card-panel {
        height: 108px;
        cursor: pointer;
        font-size: 12px;
        position: relative;
        overflow: hidden;
        color: #666;
        background: #fff;
        box-shadow: 4px 4px 40px rgba(0, 0, 0, 0.05);
        border-color: rgba(0, 0, 0, 0.05);

        &:hover {
            .card-panel-icon-wrapper {
                color: #fff;
            }

            .icon-people {
                background: #40c9c6;
            }

            .icon-message {
                background: #36a3f7;
            }

            .icon-money {
                background: #f4516c;
            }

            .icon-shopping {
                background: #34bfa3;
            }
        }

        .icon-people {
            color: #40c9c6;
        }

        .icon-message {
            color: #36a3f7;
        }

        .icon-money {
            color: #f4516c;
        }

        .icon-shopping {
            color: #34bfa3;
        }

        .card-panel-icon-wrapper {
            float: left;
            margin: 14px 0 0 14px;
            padding: 16px;
            transition: all 0.38s ease-out;
            border-radius: 6px;
        }

        .card-panel-icon {
            float: left;
            font-size: 48px;
        }

        .card-panel-description {
            float: right;
            font-weight: bold;
            margin: 26px;
            margin-left: 0px;

            .card-panel-text {
                line-height: 18px;
                color: rgba(0, 0, 0, 0.45);
                font-size: 16px;
                margin-bottom: 12px;
            }

            .card-panel-num {
                font-size: 20px;
            }
        }
    }
}

@media (max-width: 550px) {
    .card-panel-description {
        display: none;
    }

    .card-panel-icon-wrapper {
        float: none !important;
        width: 100%;
        height: 100%;
        margin: 0 !important;

        .svg-icon {
            display: block;
            margin: 14px auto !important;
            float: none !important;
        }
    }
}
</style>
