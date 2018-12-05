<template>
    <div class="productList">
        <!-- 上部分为常用产品 -->
        <div class="offenGoods">
            <div class="title">常用商品</div>
            <div class="often-goods-list">
                <ul>
                    <li v-for="oftenGood in oftenGoods">
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
                            <li>
                                <span class="goodsImg">
                                        <img src="https://via.placeholder.com/150x120" alt="">
                                  </span>
                                <span class="goodsName">食品名称</span>
                                <span class="goodsPrice">￥元</span>
                            </li>
                        </ul>
                    </div>
                </el-tab-pane>
                <el-tab-pane label="小食">
                    <div class="snack">
                    </div>
                </el-tab-pane>
                <el-tab-pane label="饮品">
                    <div class="drinks"></div>
                </el-tab-pane>
            </el-tabs>
        </div>
    </div>
</template>
<script>
export default {
    name: "productList",
    data() {
        return {
            oftenGoods: [{
                goodsId: 1,
                goodsName: '香辣鸡腿堡',
                price: 18
            }, {
                goodsId: 2,
                goodsName: '田园鸡腿堡',
                price: 15
            }, {
                goodsId: 3,
                goodsName: '和风汉堡',
                price: 15
            }, {
                goodsId: 4,
                goodsName: '快乐全家桶',
                price: 80
            }, {
                goodsId: 5,
                goodsName: '脆皮炸鸡腿',
                price: 10
            }, {
                goodsId: 6,
                goodsName: '魔法鸡块',
                price: 20
            }, {
                goodsId: 7,
                goodsName: '可乐大杯',
                price: 10
            }, {
                goodsId: 8,
                goodsName: '雪顶咖啡',
                price: 18
            }, {
                goodsId: 9,
                goodsName: '大块鸡米花',
                price: 15
            }, {
                goodsId: 20,
                goodsName: '香脆鸡柳',
                price: 17
            }],
            allGoods: [{
                goodsId: 1,
                goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg",
                goodsName: '香辣鸡腿堡',
                price: 18
            }, {
                goodsId: 2,
                goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
                goodsName: '田园鸡腿堡',
                price: 15
            }, {
                goodsId: 3,
                goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg",
                goodsName: '和风汉堡',
                price: 15
            }, {
                goodsId: 4,
                goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
                goodsName: '快乐全家桶',
                price: 80
            }, {
                goodsId: 5,
                goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
                goodsName: '脆皮炸鸡腿',
                price: 10
            }, {
                goodsId: 6,
                goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos004.jpg",
                goodsName: '魔法鸡块',
                price: 20
            }, {
                goodsId: 7,
                goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos001.jpg",
                goodsName: '可乐大杯',
                price: 10
            }, {
                goodsId: 8,
                goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos003.jpg",
                goodsName: '雪顶咖啡',
                price: 18
            }, {
                goodsId: 9,
                goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
                goodsName: '大块鸡米花',
                price: 15
            }, {
                goodsId: 20,
                goodsImg: "http://7xjyw1.com1.z0.glb.clouddn.com/pos002.jpg",
                goodsName: '香脆鸡柳',
                price: 17
            }]
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
    margin: 5px;
    background-color: #fff;
    font-size: 20px;
}
.o-price {
    font-size: 16px;
    color: #58B7FF;
}
.allGoods {
    float: left;
    width: 100%;
    background-color: #aaa;
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
    li {
        float: left;
        list-style: none;
        padding: 5px;
        margin: 10px;
        span {
            display: block;
            img {
                width: 80%;
            }
        }
            .goodsImg{
           float: left;
        }
        .goodsName {
            float: left;
            text-align: center;
            margin: 10px auto;
        }
          .goodsPrice {
            text-align: center;
            margin: 10px auto;
        }
    }
}
</style>
