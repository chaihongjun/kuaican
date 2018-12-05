<template>
    <div class="leftNav">
        <ul>
            <li><i class="iconfont icon-wodezichan"></i>
                <span>收银</span>
            </li>
            <li><i class="iconfont icon-jinrudianpu"></i>
                <span>店铺</span>
            </li>
            <li><i class="iconfont icon-hanbao"></i>
                <span>菜品</span>
            </li>
            <li><i class="iconfont icon-huiyuanqia"></i>
                <span>会员</span>
            </li>
            <li><i class="iconfont icon-31aichegujia"></i>
                <span>统计</span>
            </li>
        </ul>
    </div>
</template>
<script>
export default {
    name: "leftNav",
    data() {
        return {}
    }
}
</script>
<style>

    .leftNav{
        float: left;
        height: 100%;
    width: 15%;
    font-size: 20px;
        background-color: #409cc1;

    }
.leftNav ul{
    padding: 40px 0 0;
    margin: 0;
}


.leftNav li{
    border-bottom:1px solid #20a0ff;
    text-align: center;
    list-style-type: none;
    padding:10px 20px;

}

.leftNav li:first-child{
    border-top:1px solid #20a0ff;
}




.iconfont{
    font-size: 24px;
}

</style>
