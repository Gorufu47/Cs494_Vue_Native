<template>
  <view>  
       <button
      :on-press="restart"
      :title="start"
      
    />
        
    <text>Monster HP:{{monster}}</text>
    
    <text>{{dahero}}</text> 
     <image
          :style="{width: 200, height: 200}"
          :source="{uri: 'https://romalone.files.wordpress.com/2010/06/00c9c367e5c53d8bd8be43efbfd7b31d.gif?w=200&zoom=2'}"
        />
    
      <text>Hero HP:{{hero}}</text>

      <text>{{damoster}}</text> 
      <image
          :style="{width: 100, height: 100}"
          :source="{uri: 'https://romalone.files.wordpress.com/2010/06/722167daf91b246d91f7edebfc978e04.gif?w=258&zoom=2'}"
        />
      <button
      :on-press="atkno"
      title="โจมตีปกติ"
      color="#6666ff"
      
    /><button
      :on-press="atksp"
      title="โจมตีพิเศษ"
      color="#ff5050"
      
    />
    <text>{{msg}}</text>
  </view>
</template>

<script>
export default {
  
  data: {
    hero: "0",
    monster: "0",
    atk: "",
    spatk: "",
    highero: "",
    higmonster: "",
    msg: "",
    damoster: "",
    dahero: "",
    start: "Start Game",
    imghero: "",
    imgmonster: ""
  },
  methods: {
    onPressLearnMore: function() {
      alert("Hello");
    },
    restart:function(){
                    this.start='Restart';
                    this.hero='100';
                    this.monster='100';
                    this.msg='';
                    this.dahero='';
                    this.damoster='';
                    this.imghero='/game/hero1.gif';
                    this.imgmonster='/game/monster1.gif'
                    this.higmonster='350';
                    this.highero='400';
                },
                atkno:function(min,max){
                    //โจมตีปกติ เลือดทั้งสองไม่เท่ากับ 0
                    if(this.hero > 0 && this.monster >0){
                    this.atk = Math.max(Math.floor(Math.random() * 10) + 1, 3);
                    this.monster = this.monster - this.atk; 
                    this.dahero ='HeroHit -' + this.atk;
                    this.monsteratk = Math.max(Math.floor(Math.random() * 15) + 1, 5);
                    this.hero = this.hero - this.monsteratk;
                    this.damoster = 'MonsterHit -' +this.monsteratk;


                    this.highero = this.highero - this.monsteratk;
                    this.higmonster = this.higmonster - this.atk;
                    //เมื่อคนชนะ
                    if(this.hero >0 && this.monster <=0){
                    this.monster = '0';    
                    this.msg = alert('!!Victory!!');
                    this.imgmonster = '/game/rip.png';
                    }
                    //เมือมอนชนะ
                    if(this.hero <=0 && this.monster > 0){
                    this.hero ='0';
                    this.msg = alert('!!Lose!!');
                    this.imghero = '/game/rip.png';
                    }
                    //เมื่อเสมอ
                    if(this.hero <=0 && this.monster <=0){
                        this.hero ='0';
                        this.monster = '0'; 
                        this.msg = alert('!!เสมอ!!');
                        this.imgmonster = '/game/rip.png';
                        this.imghero = '/game/rip.png';
                    }
                   }             
                   },
                   atksp:function(min,max){
                    //โจมตีปกติ เลือดทั้งสองไม่เท่ากับ 0
                    if(this.hero > 0 && this.monster >0){
                    this.spatk = Math.max(Math.floor(Math.random() * 20) + 1,10);
                    this.monster = this.monster - this.spatk; 
                    this.dahero ='YAAA !!!Hit -' + this.spatk;
                    this.monsteratk = Math.max(Math.floor(Math.random() * 15) + 1, 5);
                    this.hero = this.hero - this.monsteratk;
                    this.damoster = 'MonsterHit -' +this.monsteratk;

                    this.highero = this.highero - this.monsteratk;
                    this.higmonster = this.higmonster - this.spatk;
                    //เมื่อคนชนะ
                    if(this.hero >0 && this.monster <=0){
                    this.monster = '0';    
                    this.msg = alert('!!Victory!!');
                    this.imgmonster = '/game/rip.png';
                    }
                    //เมือมอนชนะ
                    if(this.hero <=0 && this.monster > 0){
                    this.hero ='0';
                    this.msg = alert('!!Lose!!');
                    this.imghero = '/game/rip.png';
                    }
                    //เมื่อเสมอ
                    if(this.hero <=0 && this.monster <=0){
                        this.hero ='0';
                        this.monster = '0'; 
                        this.msg = alert('!!เสมอ!!');
                        this.imgmonster = '/game/rip.png';
                        this.imghero = '/game/rip.png';
                    }
                   }             
                   }
  }
};
</script>
 
<style>
.container {
  background-color: white;
  align-items: center;
  justify-content: center;
  flex: 1;
}
.text-color-primary {
  color: blue;
}
</style>
