<template>
  <div class="hello">
  <section id="turntable" class="gb-turntable">
        <div class="gb-turntable-container">
            <canvas class="gb-turntable-canvas" width="300" height="300px">抱歉！浏览器不支持。</canvas> 
        </div>

        <a class="gb-turntable-btn" href="javascript:;">抽奖</a>    
    </section>
   
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  method:function(){

  },
  mounted:function(){
    gbTurntable.init({
    id: 'turntable',
    config: function(callback){
        // 获取奖品信息
        callback && callback(['1元红包','2元红包','3元红包','4元红包','5元红包','6元红包']);    
    },
    getPrize: function(callback) {
        // 获取中奖信息
        var num = Math.random() * 6 >>> 0,   //奖品ID
            chances = num;  // 可抽奖次数
            callback && callback([num, chances]);   
    },
    gotBack: function(data) {
        alert('恭喜抽中' + data);
    }
    }); 
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.wrapper{
    		padding:20px 40px;
    	}
    	.fork-github{
    		position: fixed;
    		right: -100px;
    		top: 45px;
    		z-index: 9999;
    		padding: 2px 100px;
    		font-size: 12px;
    		background-color: #444;
    		border: 1px solid #000;
    		-webkit-transform: rotate(45deg);
    			-ms-transform: rotate(45deg);
    				transform: rotate(45deg);
    		text-align: center;
    	}
    	.fork-github a{
    		color: #fff;
    	}
        .gb-turntable a.gb-turntable-btn{
            border: none;
        }

</style>
