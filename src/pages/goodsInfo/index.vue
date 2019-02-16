<template>
    <div class="goodsinfo-container">
        
        <!-- 轮播图 -->
        <div class="mui-card">
            <div class="mui-card-content">
                <div class="mui-card-content-inner">
                    <swiper :banners="lunbotu"></swiper>
                </div>
            </div>
        </div>

        <!-- 商品购买区域 -->
        <div class="mui-card">
            <div class="mui-card-header">{{goodsinfo.title}} </div>
            <div class="mui-card-content">
                <div class="mui-card-content-inner">
                    <p class="price">
                        市场价:
                        <del>¥{{goodsinfo.market_price}} </del>
                        &nbsp;&nbsp;销售价:
                        <span class="now_price">¥{{goodsinfo.sell_price}} </span>
                    </p>
                    <div class="numbox">
                        <span class="title">购买数量:</span>
                        <input type="button" @click="buyCount >=2 && buyCount--" value="-" :disabled="buyCount == 1">
                        <input type="number" @change="filterMaxCount" v-model="buyCount">
                        <input type="button" @click="buyCount < goodsinfo.stock_quantity && buyCount++" value="+" :disabled="buyCount == goodsinfo.stock_quantity">
                    </div>
                    <p>
                        <mt-button type="primary" size="small">立即购买</mt-button>
                        <mt-button type="danger" size="small" @click="addToShopCar">加入购物车</mt-button>
                    </p>
                </div>
            </div>
        </div>

        <!-- 商品参数区域 -->
        <div class="mui-card">
            <div class="mui-card-header">商品参数</div>
            <div class="mui-card-content">
                <div class="mui-card-content-inner">
                    <p>商品货号:{{goodsinfo.goods_no}} </p>
                    <p>库存情况:{{goodsinfo.stock_quantity}} </p>
                    <p>上架时间:{{goodsinfo.add_time | dateFormat}} </p>
                </div>
            </div>
            <div class="mui-card-footer">
                <mt-button type="primary" size="large" plain @click="goDesc(id)">图文介绍</mt-button>
                <mt-button type="danger" size="large" plain @click="goComment(id)">商品评论</mt-button>
            </div>
        </div>
    </div>
</template>