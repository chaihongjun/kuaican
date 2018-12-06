<template>
    <div class="orderList">
        <el-tabs class="tabs">
            <el-tab-pane label="点餐">
                <el-table :data="tableData" border show-summary style="width: 100%">
                    <el-table-column prop="goodsName" label="商品"></el-table-column>
                    <el-table-column prop="count" label="数量" width="100"></el-table-column>
                    <el-table-column prop="price" label="金额" width="100"></el-table-column>
                    <el-table-column label="操作" width="100" fixed="right">
                        <template slot-scope="scope">
                            <el-button type="text" size="medium" @click="remove(scope.$index)">删除</el-button>
                            <el-button type="text" size="medium" @click="add(scope.$index)">增加</el-button>
                        </template>
                    </el-table-column>
                </el-table>
                <div class="control">
                    <el-row>
                        <el-col :span="8">
                            <el-button type="warning">挂单</el-button>
                        </el-col>
                        <el-col :span="8">
                            <el-button type="danger">删除</el-button>
                        </el-col>
                        <el-col :span="8">
                            <el-button type="success">结账</el-button>
                        </el-col>
                    </el-row>
                </div>
            </el-tab-pane>
            <el-tab-pane label="挂单"></el-tab-pane>
            <el-tab-pane label="外卖"></el-tab-pane>
        </el-tabs>
    </div>
</template>
<script>
import Bus from '@/plugins/bus.js'
export default {
    name: "orderList",
    data() {
        return {
            //点餐数据
            tableData: [],
        }
    },
    created: function() {
        var _this = this;
        // 接收来自 productList组件的数据
        Bus.$on('send', function(goods) {
            //初始化
            _this.totalCount = 0;
            _this.totalPrice = 0;
            //是否已经存在订单列表
            let isHave = false;
            for (let i = 0; i < _this.tableData.length; i++) {
                // console.log(_this.tableData[i].goodsId);
                if (_this.tableData[i].goodsId == goods.goodsId) {
                    isHave = true;
                }
            }
            //根据isHave的值判断订单列表中是否已经有此商品
            if (isHave) {
                //存在就进行数量添加
                let arr = _this.tableData.filter(o => o.goodsId == goods.goodsId);
               //  为什么是arr[0]
               //  因为只有一个数组元素，重复的元素
                // console.log(arr.length);
                arr[0].count++;
                //arr[0].price=arr[0].price*arr[0].count++;
                //console.log(arr);
            } else {
                //不存在就推入数组
                let newGoods = { goodsId: goods.goodsId, goodsName: goods.goodsName, price: goods.price, count: 1 };
                _this.tableData.push(newGoods);
            }
            //进行数量和价格的汇总计算
            _this.tableData.forEach((element) => {
                _this.totalCount += element.count;
                _this.totalMoney = _this.totalMoney + (element.price * element.count);
            });
        })
    },
    methods: {
        add: function(index) {
            this.tableData[index].count++;
        },
        remove: function(index) {
            this.tableData.splice(index, 1);
        }
    }
}
</script>
<style>
.orderList {
    height: 100%;
    background-color: #F9FaFc;
    border-right: 1px solid #c0c0ca;
}

.tabs {
    font-size: 24px;
}
</style>
<style lang="scss">
.orderList {
    .el-tabs__nav {
        display: flex;
        flex-direction: row;
        width: 100%;
    }

    .el-tabs__header {
        margin: 0;
    }

    #tab-0 {
        flex: 1;
        text-align: center;
    }

    #tab-1 {
        flex: 1;
        text-align: center;
    }

    #tab-2 {
        flex: 1;
        text-align: center;
    }

    .has-gutter {
        .cell {
            text-align: center;
        }

        .el-table__fixed-right .el-table th>.cell {
            text-align: center;
        }
    }

    .control {
        margin-top: 50px;
        text-align: center;
    }
}
</style>
