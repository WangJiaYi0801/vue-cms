<template>
    <div class="news-list-component">
        <ul class="mui-table-view">
            <li class="mui-table-view-cell mui-media" v-for="item of newsList" :key="item.id">
                <router-link :to="'/home/newsInfo/' + item.id">
                    <img class="mui-media-object mui-pull-left" :src="item.img_url">
                    <div class="mui-media-body">
                        <h1 class="title mui-ellipsis">{{item.title}}</h1>
                        <p class='mui-ellipsis'>{{item.zhaiyao}} </p>
                        <div>
                            <span>发表时间:{{item.add_time | dateFormat}}</span>
                            <span>点击{{item.click}}次</span>
                        </div>
                    </div>
                </router-link>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    data(){
        return{
            newsList:[]
        };
    },
    created(){
        this.getNewsList();
    },
    methods:{
        getNewsList(){
            this.$http.get("getNewsList").then(result =>{
                this.newsList = result.body.message;
            });
        }
    },
};
</script>

<style lang="less" scoped>
    .news-list-component{
        .mui-media-body{
            .title{
                font-size: 16px;
            }
            div{
                display: flex;
                justify-content: space-between;
                span{
                    font-size: 12px;
                    color: #26a2ff;
                }
            }
        }
    }
</style>
