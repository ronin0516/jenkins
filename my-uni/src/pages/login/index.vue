<template>
    <view class="login-wrap">
        <view class="login-icon">
            <img class="login-icon_img" src="/static/logo.png"/>
        </view>
        <button open-type="getUserInfo" @getuserinfo="getUserInfo">登录</button>
            
    </view>
</template>

<script>
export default {
    props: {

    },
    data() {
        return {

        };
    },
    computed: {

    },
    created() {

    },
    mounted() {

    },
    watch: {

    },
    methods: {
        getUserInfo(){
            let p = new Promise((resolve, reject) => {
                uni.login({
                    provider: 'weixin',
                    success(res){
                        resolve(res)
                    },
                    fail(err) {
                        reject(err)
                    }
                })
            }).then(res => {
                uni.getUserInfo({
                    provider: 'weixin',
                    success(userInfo) {
                        
                        uni.setStorageSync('userInfo', userInfo.userInfo)
                        uni.setStorageSync('login', true);
                        uni.switchTab({url: '/pages/center/mine/index'})
                        console.log('userinfouserinfo', userInfo)
                    }
                })
                console.log("打印用户信息", res)
                // }
            })
            
            
        }
    },
    components: {

    },
};
</script>

<style scoped lang="scss">
</style>
