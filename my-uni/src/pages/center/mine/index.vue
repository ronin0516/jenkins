<template>
    <view class="content">
        <view class="header" @click="login">
            <image class="header-image" :src="userInfo.avatarUrl"/>
            <view class="header-name">{{userInfo.nickName}}</view>
        </view>
        
        <view class="body">
            <view class="list-wrap">
                <view class="list">
                    <view class="item" v-for="(item,index) in list" :key="index">{{item}}</view>
                </view>
            </view>
        </view>   
        <view>vue过滤器 {{Date.now() | formatDate}}</view>
    </view>
</template>

<script>
export default {
    props: {

    },
    data() {
        return {
            userInfo: {
                name: 'uni-app',
            },
            list: [1,2,3,4,5,6]
        };
    },
    computed: {

    },
    filters: {
        formatDate(value) {
            let d = new Date(value);
            let year = d.getFullYear();
            let month = d.getMonth() + 1 > 9 ? d.getMonth()+1 : '0' + (d.getMonth()+1);
            let date = d.getDate() > 9 ? d.getDate() : '0' + d.getDate();
            return `${year}-${month}-${date}`
        }
    },
    onShow(){
        console.log("请求后端接口--onshow")
    },
    onLoad(){
        console.log("请求后端接口")
        uni.request({
            url: 'http://localhost:3000/users/userInfo',
            data: {name: '倪梦玉'},
            method: 'get',
            complete: ({data}) => {
                console.log("打印结果", data)
            }
        })

        this.userInfo = uni.getStorageSync('userInfo')
    },
    created() {
        console.log("请求后端接口--created")
    },
    mounted() {

    },
    watch: {

    },
    methods: {
        login(){
            uni.navigateTo({url: '/pages/login/index'})
        }
    },
    components: {

    },
};
</script>

<style scoped>
    .content{
        width: 100%;
        height: 100%;
        
    }
    .header{
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding:20rpx 40rpx;
        /* width: 100%; */
        height: 200upx;
        background:  #c1c1c1;
    }
    .header-image{
            width: 100upx;
            height: 100upx;
            border-radius: 50%;
        }
    .header-name{
            font-size: 32upx;
            color: #333;
            text-align: center;
        }
        .list{
            padding: 0 40upx;
        }
    .item{
        height: 100upx;
        line-height: 100upx;
        font-size: 32upx;
        border-bottom: 2upx solid #c1c1c1;
    }
</style>
