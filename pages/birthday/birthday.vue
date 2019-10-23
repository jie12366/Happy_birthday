<template>
    <view :class="[{peach: turn_on}, {'peach-after': decorate}]" :style="{'background-color': bg_color}">
        <!--气球-->
        <view class="balloons text-center b1-fly" id="b1" v-show="cake" :class="{'balloons-rotate-behaviour-one': cake}">
        </view>
        <view class="balloons text-center b2-fly" id="b2" v-show="cake" :class="{'balloons-rotate-behaviour-two': cake}">
        </view>
        <view class="balloons text-center b3-fly" id="b3" v-show="cake" :class="{'balloons-rotate-behaviour-two': cake}">
        </view>
        <view class="balloons text-center b4-fly" id="b4" v-show="cake" :class="{'balloons-rotate-behaviour-one': cake}">
        </view>
        <view class="balloons text-center b5-fly" id="b5" v-show="cake" :class="{'balloons-rotate-behaviour-one': cake}">
        </view>
        <view class="balloons text-center b6-fly" id="b6" v-show="cake" :class="{'balloons-rotate-behaviour-two': cake}">
        </view>
        <view class="balloons text-center b7-fly" id="b7" v-show="cake" :class="{'balloons-rotate-behaviour-one': cake}">
        </view>

        <image src="http://cdn.jie12366.xyz/Balloon-Border.png" width="100%" class="balloon-border"></image>
        
        <!--灯-->
        <view class="light">
            <view class="bulb-holder">
                <view class="bulb" :class="[{'bulb-glow-yellow': turn_on}, {'bulb-glow-yellow-after': decorate}]" id="bulb_yellow"></view>
            </view>
            <view class="bulb-holder">
                <view class="bulb" :class="[{'bulb-glow-red': turn_on}, {'bulb-glow-red-after': decorate}]" id="bulb_red"></view>
            </view>
            <view class="bulb-holder">
                <view class="bulb" :class="[{'bulb-glow-blue': turn_on}, {'bulb-glow-blue-after': decorate}]" id="bulb_blue"></view>
            </view>
            <view class="bulb-holder">
                <view class="bulb" :class="[{'bulb-glow-green': turn_on}, {'bulb-glow-green-after': decorate}]" id="bulb_green"></view>
            </view>
            <view class="bulb-holder">
                <view class="bulb" :class="[{'bulb-glow-pink': turn_on}, {'bulb-glow-pink-after': decorate}]" id="bulb_pink"></view>
            </view>
            <view class="bulb-holder">
                <view class="bulb" :class="[{'bulb-glow-orange': turn_on}, {'bulb-glow-orange-after': decorate}]" id="bulb_orange"></view>
            </view>
        </view>
        <view class="text-center">
            <image src="http://cdn.jie12366.xyz/banner.png" class="bannar" :class="{'bannar-come': fly}">
        </view>
        <!--蛋糕-->
        <view class="cake-cover">
            <view class="texr-center">
                <view class="cake" v-show="candle">
                    <view class="velas">
                        <view class="fuego" v-show="birthday"></view>
                        <view class="fuego" v-show="birthday"></view>
                        <view class="fuego" v-show="birthday"></view>
                        <view class="fuego" v-show="birthday"></view>
                        <view class="fuego" v-show="birthday"></view>
                    </view>
                    <view class="cobertura"></view>
                    <view class="bizcocho"></view>
                </view>
            </view>
        </view>
        <view class="message">
            <text>Today is...</text>
        </view>
        <!--底部控制按钮-->
        <view class="buttom-button">
            <view style="text-align: center;">
                <button class="btn-primary" id="turn_on" @click="turnOn()" v-if="!turn_on1">开灯</button>
                <button class="btn-primary" id="play" @click="play_music()" v-if="play">来点音乐</button>
                <button class="btn-primary" id="bannar_coming" @click="bannar_coming()" v-if="decorate1">装饰一下吧</button>
                <button class="btn-primary" id="balloons_flying" @click="balloons_flying()" v-if="fly1">放飞气球</button>
                <button class="btn-primary" id="cake_fadein" @click="cake_fadein()" v-if="cake1">打开美味的蛋糕</button>
                <button class="btn-primary" id="light_candle" @click="light_candle()" v-if="candle1">点上蜡烛</button>
                <button class="btn-primary" id="wish_message" @click="wish_message()" v-if="birthday1">生日快乐!</button>
                <!-- <button class="btn btn-primary" id="cake_cut">Lrt's Cut the Cake</button> -->
            </view>
        </view>
    </view>
</template>

<script>
    export default {
        data() {
            return {
                turn_on: false,
                turn_on1: false,
                play: false,
                decorate: false,
                decorate1: false,
                fly: false,
                fly1: false,
                cake: false,
                cake1: false,
                candle: false,
                candle1: false,
                birthday: false,
                birthday1: false,
                bg_color: null
            }
        },
        methods: {
            // 开灯
            turnOn () {
                this.turn_on = true
                this.turn_on1 = true
                var that = this
                setTimeout(function() {
                    that.play = true
                }, 3000)
            },
            // 播放音乐
            play_music () {
                this.play = false
                // 定义背景音频管理器
                const bgAudioMannager = uni.getBackgroundAudioManager()
                bgAudioMannager.title = '走过绿意';
                bgAudioMannager.singer = 'Kevin Kern';
                bgAudioMannager.coverImgUrl = 'http://i.htqyy.com/img7/0/149.jpg';
                bgAudioMannager.src = 'http://cdn.jie12366.xyz/play.mp3'
                bgAudioMannager.loop = true // 设置循环播放
                bgAudioMannager.play()
                this.decorate = true
                this.bg_color = '#fff'
                var that = this
                setTimeout(function() {
                    that.decorate1 = true
                }, 3000)
            },
            // 开始装饰
            bannar_coming () {
                this.decorate1 = false
                this.fly = true
                var that = this
                setTimeout(function() {
                    that.fly1 = true
                }, 3000)
            },
            // 放飞气球
            balloons_flying () {
                this.fly1 = false
                this.cake = true
                var that = this
                setTimeout(function() {
                    that.cake1 = true
                }, 3000)
            },
            // 打开蛋糕
            cake_fadein () {
                this.cake1 = false
                this.candle = true
                var that = this
                setTimeout(function() {
                    that.candle1 = true
                }, 3000)
            },
            // 点蜡烛
            light_candle () {
                this.candle1 = false
                this.birthday = true
                var that = this
                setTimeout(function() {
                    that.birthday1 = true
                }, 3000)
            },
            // 想说的一些话
            wish_message () {
                
            }
        }
    }
</script>

<style>
    @import '../../style/stylesheet.css';
    @import '../../style/loading.css';
    @import '../../style/cake.css';
</style>
