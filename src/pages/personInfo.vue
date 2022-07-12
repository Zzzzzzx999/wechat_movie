<template>
  <div class="personInfoForm">
        <div class="basicInfo">
            <div class="infoItem">
                <span>姓名:</span>  
                <input :style="{'text-align':personInfo.name ? 'left' : 'right'}" v-model="personInfo.name" type="text" placeholder="未填写">
            </div> 
            <div class="infoItem">
                <span>昵称: </span> 
                <input :style="{'text-align':personInfo.nickname ? 'left' : 'right'}" v-model="personInfo.nickname" type="text" placeholder="未填写">
            </div> 
            <div class="infoItem">
                <span>性别: </span> 
                <picker range-key="name" @change="bindPickerChangeSex" :value="userSex" :range="userSex">
                    <view class="picker" v-if="userSexIndex>=0">
                        <text>{{userSex[userSexIndex].name}}</text>
                    </view>
                    <view v-show="userSexIndex===-1" style="text-align:right;width:70vw;color:gray">
                        <text>未填写</text>
                    </view>
                </picker>
            </div> 
            <div class="infoItem">
                <span>年龄: </span> 
                <input :style="{'text-align':personInfo.age ? 'left' : 'right'}" v-model="personInfo.age" type="number" placeholder="未填写">
            </div> 
            <div class="infoItem">
                <span>生日: </span> 
                <!-- <input type="text" placeholder="未填写" > -->
                <picker mode="date" :value="date" start="1960-01-01" end="2022-04-01" @change="bindDateChange">
                    <view class="picker" v-show="dateIndex>=0">
                        <text>{{date}}</text>
                    </view>
                    <view v-show="dateIndex===-1" style="text-align:right;width:70vw;color:gray">
                        <text>未填写</text>
                    </view>
                </picker>
            </div>
            <div class="infoItem">
                <span>星座: </span>
                <picker range-key="name" @change="bindPickerChangeConstellation" :value="constellationIndex" :range="constellation">
                    <view class="picker" v-if="constellationIndex>=0">
                        <text>{{constellation[constellationIndex].name}}</text>
                    </view>
                    <view v-show="constellationIndex===-1" class="notWrite" style="text-align:right;width:70vw;color:gray">
                        <text>未填写</text>
                    </view>
                </picker>
            </div>
        </div>
        <div class="otherInfo">
            <div class="infoItem">
                <span>公司: </span> 
                <input :style="{'text-align':personInfo.company ? 'left' : 'right'}" v-model="personInfo.company" type="text" placeholder="未填写">
            </div>
            <div class="infoItem">
                <span>学校: </span> 
                <input :style="{'text-align':personInfo.school ? 'left' : 'right'}" v-model="personInfo.school" type="text" placeholder="未填写">
            </div>
            <div class="infoItem">
                <span>手机号码: </span> 
                <input :style="{'text-align':personInfo.telephoneNumber ? 'left' : 'right'}" v-model="personInfo.telephoneNumber" type="text" placeholder="未填写" maxlength="11">
            </div>
            <div class="infoItem">
                <span>邮箱: </span> 
                <input :style="{'text-align':personInfo.email ? 'left' : 'right'}" v-model="personInfo.email" type="text" placeholder="未填写">
            </div>
            <div class="infoItem personalSignature">
                <span>个性签名: </span> 
                <input :style="{'text-align':personInfo.Signature ? 'left' : 'right'}" v-model="personInfo.Signature" type="text" placeholder="未填写">
            </div>
        </div>
        <div class="saveInfo">
            <button @click="saveInfomation">保存</button>
        </div>
  </div>
</template>

<script>
export default {
    name:'personInfo',
    data() {
        return {
            personInfo:{
                name:'',
                nickname:'',
                age:'',
                company:'',
                school:'',
                telephoneNumber:'',
                email:'',
                Signature:''
            },
            userSexIndex:-1,
            userSex:[
                {id:1,name:'男'},
                {id:2,name:'女'}
            ],
            constellationIndex: -1,
            constellation:[
                {id:1,name:'白羊座'},
                {id:2,name:'金牛座'},
                {id:3,name:'双子座'},
                {id:4,name:'巨蟹座'},
                {id:5,name:'狮子座'},
                {id:6,name:'处女座'},
                {id:7,name:'天秤座'},
                {id:8,name:'天蝎座'},
                {id:9,name:'射手座'},
                {id:10,name:'摩羯座'},
                {id:11,name:'水瓶座'},
                {id:12,name:'双鱼座'}
            ],
            date: '2016-09-01',
            dateIndex:-1,
        }
    },
    methods: {
        saveInfomation(){
            let userInfo = {
                name: this.personInfo.name
            }
            wx.setStorageSync('userInfo', userInfo)
            wx.navigateBack()
        },
       /*  myPhoneNumber(){
            
        }, */
        bindPickerChangeConstellation(e) {
            console.log(e)
            this.constellationIndex = e.detail.value
        },
        /* bindDateChange(e) {
            console.log(e);
            console.log('picker发送选择改变,携带值为', e.detail.value)
            this.setData({                                              ////////???????
                date: e.detail.value
            })
        }, */
        bindDateChange(e) {
            console.log(e);
            console.log('picker发送选择改变，携带值为', e.detail.value)
            this.date=e.detail.value
            this.dateIndex=1
        },
        /* bindDateChange:((e)=>{
            console.log(e);
            this.setData({
                date: e.detail.value
            })
        }), */
        bindPickerChangeSex(e) {
            console.log(e)
            this.userSexIndex = e.detail.value
        },
        bindMultiPickerChange(e) {
            console.log('picker发送选择改变,携带值为', e.detail.value)
            this.setData({
                multiIndex: e.detail.value
            })
        },
    },
    onShow: function() {
        console.log('App Show')
        console.log(this.background);
        if (wx.getStorageSync('background')) {
            this.background = wx.getStorageSync('background')
            this.bgcolor=this.background.color
        }
        wx.setNavigationBarColor({      // 窗口的背景色
            frontColor: '#000000',
            backgroundColor: this.bgcolor
        });
        wx.setBackgroundColor({
            backgroundColor: this.bgcolor, // 窗口的背景色为白色
        })
    },
}
</script>

<style>
body{
    background-color: whitesmoke;
}
.basicInfo{
    background-color: white;
    height: 490rpx;
    width: 100%;
}
.otherInfo{
    background-color: white;
}
.infoItem{
    display: flex;
    justify-content: flex-start;
    align-items: center;
    margin-left: 35rpx;
    padding-right: 35rpx;
    background-color: white;
    height: 80rpx;
    border-bottom: 1rpx solid rgb(240, 239, 239);
}
.infoItem span{
    text-align: left;
    width: 25%;
    font-size: 36rpx;
    font-weight: 600;
}
.infoItem input{
    width: 75%;
    font-size: 32rpx;
    text-align: left;
}
.infoItem text{
    font-size: 32rpx;
}

.saveInfo{
    margin: 100rpx 200rpx 0 200rpx;
}
button{
    background-color: #8FBC8F;
}
.otherInfo{
    margin-top: 20rpx;
}
.personalSignature{
    margin-top: 20rpx;
}
.notWrite{
    text-align:right;
    width:70vw;
    color:gray;
}
.saveInfo button{
    color: white;
    margin-bottom: 40rpx;
    height: 105rpx;
    width: 250rpx;
}
</style>