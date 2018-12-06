<template>
    <div class="productList">
        <!-- 上部分为常用产品 -->
        <div class="offenGoods">
            <div class="title">常用商品</div>
            <div class="often-goods-list">
                <ul>
                    <li v-for="oftenGood in oftenGoods" @click="selectFood(oftenGood)">
                        <span>{{oftenGood.goodsName}}</span>
                        <span class="o-price">￥{{oftenGood.price}}元</span>
                    </li>
                </ul>
            </div>
        </div>
        <!-- 下部为所有产品（有分类） -->
        <div class="allGoods">
            <el-tabs>
                <el-tab-pane label="主食">
                    <div class="staple">
                        <ul>
                            <li v-for="staple in staples" @click="selectFood(staple)">
                                <span class="goodsImg">
                                        <img src="https://via.placeholder.com/120x100" alt="">
                                  </span>
                                <span class="goodsName">{{staple.goodsName}}</span>
                                <span class="goodsPrice">￥{{staple.price}}元</span>
                            </li>
                        </ul>
                    </div>
                </el-tab-pane>
                <el-tab-pane label="小食">
                    <div class="snack">
                        <ul>
                            <li v-for="snack in snacks" @click="selectFood(snack)">
                                <span class="goodsImg">
                                        <img src="https://via.placeholder.com/120x100" alt="">
                                  </span>
                                <span class="goodsName">{{snack.goodsName}}</span>
                                <span class="goodsPrice">￥{{snack.price}}元</span>
                            </li>
                        </ul>
                    </div>
                </el-tab-pane>
                <el-tab-pane label="饮品">
                    <div class="drinks">
                        <ul>
                            <li v-for="drink in drinks" @click="selectFood(drink)">
                                <span class="goodsImg">
                                        <img src="https://via.placeholder.com/120x100" alt="">
                                  </span>
                                <span class="goodsName">{{drink.goodsName}}</span>
                                <span class="goodsPrice">￥{{drink.price}}元</span>
                            </li>
                        </ul>
                    </div>
                </el-tab-pane>
                <el-tab-pane label="套餐">
                    <div class="packages">
                        <ul>
                            <li v-for="packageset in packages" @click="selectFood(packageset)">
                                <span class="goodsImg">
                                        <img src="https://via.placeholder.com/120x100" alt="">
                                  </span>
                                <span class="goodsName">{{packageset.goodsName}}</span>
                                <span class="goodsPrice">￥{{packageset.price}}元</span>
                            </li>
                        </ul>
                    </div>
                </el-tab-pane>
            </el-tabs>
        </div>
    </div>
</template>
<script>
import Bus from '@/plugins/bus.js'
import axios from 'axios'
export default {
    name: "productList",
    data() {
        return {
            oftenGoods: [],
            //主食类数据
            staples: [],
            //小食
            snacks: [],
            // 饮料
            drinks: [],
            // 套餐
            packages: []
        }
    },
    mounted: function() {
        var height = document.body.clientHeight || document.documentElement.clientHeight;
        document.getElementById('productList').style.height = height + 'px';
    },
    created: function() {
        //获取常用食品
        axios.get('https://www.easy-mock.com/mock/5b8b30dbf032f03c5e71de7f/kuaican/oftenGoods')
            .then(response => {
               // console.log(response);
                this.oftenGoods = response.data;
               // console.log('oftenGoods:' + this.oftenGoods);
            })
            .catch(error => {
               // console.log(error);
                alert('网络错误，不能访问1');
            })
        //分别获取各类型食品
        axios.get('https://www.easy-mock.com/mock/5b8b30dbf032f03c5e71de7f/kuaican/typeGoods')
            .then(response => {
             //   console.log(response);
                //获取主食
                this.staples = response.data[0];
              //  console.log('staples:' + this.staples);
                // 获取小食
                this.snacks = response.data[1];
              //  console.log('snacks:' + this.snacks);
                //获取 饮品
                this.drinks = response.data[2];
               // console.log('drinks:' + this.drinks);
                // 获取套餐
                this.packages = response.data[3];
              //  console.log('packages:' + this.packages);
            })
            .catch(error => {
              //  console.log(error);
                alert('网络错误，不能访问2');
            })
    },
    methods: {
        //将选择的商品数据 发送到 orderlist组件
        selectFood: function(goods) {
            Bus.$emit('send', goods)
        }
    }
}
</script>
<style>
.productList {
    float: left;
    width: 100%;
}

.offenGoods {
    float: left;
    width: 100%;
    background-color: #ddd;
}

.offenGoods .title {
    text-align: center;
}

.often-goods-list ul {
    padding: 0;
    margin: 0;
}

.often-goods-list li {
    list-style-type: none;
    float: left;
    border: 1px solid #E5E9F2;
    padding: 10px;
    margin: 10px;
    background-color: #fff;
    font-size: 20px;
}

.often-goods-list li:hover {
    cursor: pointer;
}

.o-price {
    font-size: 16px;
    color: #58B7FF;
}

.allGoods {
    float: left;
    width: 100%;
    height: 100%;
    background-color: #aaa;
}

.allGoods li {
    border: 1px solid #eee;
}

.allGoods li:hover {
    cursor: pointer;
}
</style>
<style lang="scss">
.allGoods {
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

    #tab-3 {
        flex: 1;
        text-align: center;
    }

    li {
        float: left;
        list-style: none;
        padding: 5px;
        margin: 10px;
        background-color: #fff;

        span {
            display: block;

            img {
                display: block;
            }
        }

        .goodsImg {
            float: left;
        }

        .goodsName {
            float: left;
            text-align: center;
            margin: 10px;
        }

        .goodsPrice {
            text-align: center;
            margin: 10px;
        }
    }

    .el-tabs__content {
        height: 100%;
    }
}
</style>
