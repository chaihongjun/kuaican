<template>
    <div class="home">
        <!-- 左侧导航菜单部分  -->
        <leftNav></leftNav>
        <!-- 右侧操作区域  -->
        <div class="main">

            <el-row>
              <!-- 订单操作栏目 -->
                <el-col :span="8">
                    <orderList></orderList>
                </el-col>
                <!-- 商品展示栏目 -->
                <el-col :span="16">
                    <productList></productList>
                </el-col>

            </el-row>
        </div>
    </div>
</template>
<script>
// @ is an alias to /src
import leftNav from '@/components/leftNav'
import orderList from '@/components/orderList'
import productList from '@/components/productList'
export default {
    name: 'home',
    components: {
        leftNav,
        orderList,
        productList
    }
}
</script>
<style>
.home {
    height: 100%;
}
.main{
  float: left;
  width: 85%;
   height: 100%;
}
</style>
