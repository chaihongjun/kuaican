<template>
    <div class="orderList" id="orderList">
        <el-tabs class="tabs">
            <el-tab-pane label="点餐">
                <el-table :data="tableData" border stripe show-summary style="width: 100%">
                    <el-table-column prop="goodsName" label="商品"></el-table-column>
                    <el-table-column prop="count" label="数量" width="80"></el-table-column>
                    <el-table-column prop="price" label="金额" width="100"></el-table-column>
                    <el-table-column label="操作" width="150" fixed="right">
                        <template scope="scope">
                            <el-button type="text" size="small">删除</el-button>
                            <el-button type="text" size="small">增加</el-button>
                        </template>
                    </el-table-column>
                </el-table>
            </el-tab-pane>
            <el-tab-pane label="挂单"></el-tab-pane>
            <el-tab-pane label="外卖"></el-tab-pane>
        </el-tabs>
    </div>
</template>
<script>
export default {
    name: "orderList",
    data() {
        return {}
    },
    mounted: function() {
        var height = document.body.clientHeight || document.documentElement.clientHeight;
        document.getElementById('orderList').style.height = height + 'px';
    }
}
</script>
<style>
.orderList {
    height: 100%;
    background-color: #ccc;
    border-right: 1px solid #4F5FEc;
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
}
</style>
