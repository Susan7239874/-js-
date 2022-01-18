
由https://github.com/baqihg/wxTimer 这个所改的！  
改前用于：小程序   
改完用于：html渐入式vue  

引入js文件
```
<script src="具体看项目把wxTimer.js放哪儿"></script>
```
//开启一个定时器
```
var wxTimer1 = new timer({  
    beginTime:"00:00:10",  
    name:'wxTimer1',  
    complete:function(){  
        console.log("完成了")  
    }  
})  
wxTimer1.start(this);//开启定时器  

wxTimer.stop();//关闭定时器  
```
注意：//下面这2个要写在vue的data中，不然报错  
```
wxTimerList:{},  
timerObj:{},  
```
使用方法：  
 ```
<div id="app">   
 <div>显示剩余时间：{{timerObj.wxTimer}}</div>   
 <div>显示剩余秒数：{{timerObj.wxTimerSecond}}</div>   
  </div>    
  
data:{    
            timer:null,    
            wxTimerList:{},  
            timerObj:{},  
            },  
            methods:{    
            closefn(){//关闭定时器    
               this.timer.stop();    
            }  
            },  
            created:{  
                    let duration=60 //60分钟  
                    let duration2=parseInt(duration/60)+':'+ duration%60+':00'//把60分钟换算为01:00:00的格式  
                    this.timer=new wxTimer({   
                        beginTime:duration2,//格式"00:10:00"  
                        name:'timer',  
                        complete:function(){  
                            Ealert({  
                                title:'提示',  
                                message:'考试时间结束！'  
                            })  
                        }  
                    })  
                    this.timer.start(this);  
            }  
```
