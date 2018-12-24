<template>
    <div>
      <i-card title="卡片标题" extra="额外内容" thumb="https://i.loli.net/2017/08/21/599a521472424.jpg">
        <view slot="content">内容不错</view>
        <view slot="footer">
          <div class="down">
            <span>首单减7</span>
            <i-icon type="unfold" size="12" color="#80848f"></i-icon>
          </div>
        </view>
      </i-card>
      <i-tabs  :current="current_scroll" color="#f759ab" scroll :change="handleChangeScroll">
        <i-tab key="tab1" title="点菜"></i-tab>
        <i-tab key="tab2" title="评价"></i-tab>
        <i-tab key="tab3" title="商家"></i-tab>
      </i-tabs>
      <div class="tab">
        <div class="tabBar">
        <scroll-view scroll-y="true">
              <div v-for="(t,index) in tabBar" class="tabName" @click="select(index)" :class="{select:t===name}" >
                {{t}}
              </div>
        </scroll-view>
      </div>
          <div class="foodPanel" >
            <div class="text">{{name}}</div>
            <scroll-view scroll-y="true" style="height:1024rpx" @scroll="scroll"
                         :scroll-into-view="current" scroll-with-animation="false" >
              <div v-for="(item,index) in items" :id="item.category">
                <div class="textOne" v-if="item.name!==name" >{{item.name}}</div>
                <div class="food" v-for="(c,idx) in item.choice" :key="idx">
                  <div class="foodImg"></div>
                  <div class="message">
                    <div style="font-weight: bold">{{c.name}}</div>
                    <div class="detail">{{c.describe}}</div>
                    <div>月售 <span style="color: red">{{c.sale}}</span>
                      赞 <span style="color: red">{{c.like}}</span>
                    </div>
                    <div class="messageSelect">
                      <div>￥{{c.price}}起</div>
                      <div>选规格</div>
                    </div>
                  </div>
                </div>
              </div>
            </scroll-view>
          </div>
      </div>
    </div>
</template>

<script>
  export default {

    data:function() {
      return{
        current_scroll: 'tab1',
        current:'c0',
        num:0,
        name:'热销',
        tabBar:[
          "热销",
          "精品点心",
          "现做大包",
          "美味糕点",
          "可口炸品",
          "饮料",
          "香煎",
          "超级套餐",
          "生鲜类",
        ],
        choice:[
          {name:'春卷',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
          {name:'招牌叉烧包',describe:'我的家，你的家，我们大家的家，全部都吃叉烧包',sale:'123',like:'4',price:'2'},
          {name:'瑶柱糯米鸡',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
          {name:'流沙包',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
          {name:'玉米肉饺',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
        ],
        items:[
          {category:'c0',name:"热销",choice:[
              {name:'春卷',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'招牌叉烧包',describe:'我的家，你的家，我们大家的家，全部都吃叉烧包',sale:'123',like:'4',price:'2'},
              {name:'瑶柱糯米鸡',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'流沙包',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'玉米肉饺',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
            ]},
          {category:'c1',name:"精品点心",choice:[
              {name:'春卷',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'招牌叉烧包',describe:'我的家，你的家，我们大家的家，全部都吃叉烧包',sale:'123',like:'4',price:'2'},
              {name:'瑶柱糯米鸡',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'流沙包',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'玉米肉饺',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
            ]},
          {category:'c2',name:"现做大包",choice:[
              {name:'春卷',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'招牌叉烧包',describe:'我的家，你的家，我们大家的家，全部都吃叉烧包',sale:'123',like:'4',price:'2'},
              {name:'瑶柱糯米鸡',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'流沙包',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'玉米肉饺',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
            ]},
          {category:'c3',name:"美味糕点",choice:[
              {name:'春卷',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'招牌叉烧包',describe:'我的家，你的家，我们大家的家，全部都吃叉烧包',sale:'123',like:'4',price:'2'},
              {name:'瑶柱糯米鸡',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'流沙包',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'玉米肉饺',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
            ]},
          {category:'c4',name:"可口炸品",choice:[
              {name:'春卷',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'招牌叉烧包',describe:'我的家，你的家，我们大家的家，全部都吃叉烧包',sale:'123',like:'4',price:'2'},
              {name:'瑶柱糯米鸡',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'流沙包',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'玉米肉饺',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
            ]},
          {category:'c5',name:"饮料",choice:[
              {name:'春卷',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'招牌叉烧包',describe:'我的家，你的家，我们大家的家，全部都吃叉烧包',sale:'123',like:'4',price:'2'},
              {name:'瑶柱糯米鸡',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'流沙包',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'玉米肉饺',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
            ]},
          {category:'c6',name:"香煎",choice:[
              {name:'春卷',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'招牌叉烧包',describe:'我的家，你的家，我们大家的家，全部都吃叉烧包',sale:'123',like:'4',price:'2'},
              {name:'瑶柱糯米鸡',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'流沙包',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'玉米肉饺',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
            ]},
          {category:'c7',name:"超级套餐",choice:[
              {name:'春卷',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'招牌叉烧包',describe:'我的家，你的家，我们大家的家，全部都吃叉烧包',sale:'123',like:'4',price:'2'},
              {name:'瑶柱糯米鸡',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'流沙包',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'玉米肉饺',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
            ]},
          {category:'c8',name:"生鲜类",choice:[
              {name:'春卷',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'招牌叉烧包',describe:'我的家，你的家，我们大家的家，全部都吃叉烧包',sale:'123',like:'4',price:'2'},
              {name:'瑶柱糯米鸡',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'流沙包',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
              {name:'玉米肉饺',describe:'外皮酥脆，馅料鲜香',sale:'123',like:'4',price:'2'},
            ]},
        ],
        position:[],
        first:0,
      }
    },

    methods:{
      handleChangeScroll ({detail}) {
        this.current_scroll =detail.key;
      },
      select(t) {
        this.current = "c"+t;
        this.num = t;
        this.name = this.tabBar[t];
        console.log(this.name);
      },
      checkPosition:function(){
        let me = this;
        wx.createSelectorQuery().select("#c0").boundingClientRect(function(rect) {
          me.first = rect.top;
        }).exec();
        wx.createSelectorQuery().selectAll('.textOne').boundingClientRect(function(rects) {
          rects.forEach(function(rect) {
            me.position.push(rect.top);
          })
        }).exec();
      },
      scroll(e){
        console.log(JSON.stringify(this.position));
        let length = e.mp.detail.scrollTop+this.first;
        console.log(length);

        for(let i in this.position){
            if(length<this.position[0]){
              this.name = this.tabBar[0];
              break;
            }else if(length>this.position[i-1] && length<=this.position[i]){
              this.name = this.tabBar[i];
              break;
            }else if(length>this.position[i]){
              this.name = this.tabBar[i++];
            }
        }
        // if(length> this.position[this.position.length]) this.name = this.tabBar[this.position.length+1];
      },
    },
    mounted:function() {
        this.checkPosition();

    }
  };
</script>

<style scoped>
  .down{
    display: flex;
    flex-direction: row;
    flex-wrap: inherit;
    justify-content: space-between;
  }
  .select{
    color: #f759ab;
  }
  .tab{
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
  }
  .tabBar{
    display: flex;
    flex-direction: column;
   /* width: 160rpx;*/
    font-size: 30rpx;
    background-color: #ececec;
  }
  .tabName{
    height: 50rpx;
    color: #6c757d;
    padding: 20rpx;
  }
  .select{
    background-color: #fff;
/*    padding: -20rpx;*/
  }
  .foodPanel{
    display: flex;
    flex-direction: column;
    font-size: 30rpx;
    margin-left: 20rpx;
  }
  .food{
    display: flex;
    flex-direction: row;
    padding: 10rpx;
    margin-bottom: 20rpx;
  }
  .message{
    display: flex;
    flex-direction: column;
    margin-left: 20rpx;
  }
  .message>div{
    margin-bottom: 10rpx;
    width: 300rpx;
  }
  .text{
    height: 50rpx;
    padding: 20rpx 0 20rpx 0;
  }
  .textOne{
    padding-bottom: 20rpx;
  }
  .detail{
    width: 180rpx;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .messageSelect{
    display: flex;
    flex-direction: row;
  }
  .foodImg{
      height: 150rpx;
      width: 150rpx;
      background-color: #1c7430;
      padding: 20rpx;
  }
  .messageSelect{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
</style>
