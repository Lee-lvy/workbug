# workbug
前端工作日常积累
学习网站：
https://github.com/goodjack/developer-roadmap-chinese

https://blog.csdn.net/qq_34348873/article/details/52572008

https://github.com/dypsilon/frontend-dev-bookmarks

https://github.com/JacksonTian/fks

http://www.ichartjs.com/samples/index.html?page=pie3d_02.html&pageno=7

https://blog.csdn.net/apeng_1102/article/details/50740436

https://developer.mozilla.org/zh-CN/docs/Web

https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/00143449934543461c9d5dfeeb848f5b72bd012e1113d15000

https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Closures

app文档地址：https://svn:8443/svn/PXB_doc/app

原生 js

1.监听事件 e.target 点击其他区域的时候搜索框消失
document.body.addEventListener("click",function (e) {
     var search_select = document.getElementById('search_select');
     var search_input = document.getElementById('search_input');
     var searchgo_icon = document.getElementById('searchgo_icon');
     if (e.target !== search_select && e.target !== search_input){
         $vm.unsearch = true;
     }
    if (e.target == searchgo_icon){
      $vm.unsearch = false;
    }
  });


2.监听事件 keydown 回车搜索
var search_input = document.getElementById('search_input');
  search_input.addEventListener('keydown',function (e) {
    if (e.keyCode == 13) {
      $vm.go_search();
    }
  })；

   jQuery方法：
	$('#applyCertNum').bind('keypress',function(event){ 

        	 if(event.keyCode == 13){  

             	alert('你输入的内容为1：' + $('#applyCertNum').val()); 
 
        	 }  

     	});

3.监听事件 失去焦点
var search_input = document.getElementById('search_input');
search_input.addEventListener('blur',function(){
	console.log('失去焦点');
});

<input type="text" name="test1" value="test1" onblur=alert("可以关掉aaaaaaa!")> （注：在页面中）

4.获取焦点/失去焦点
document.getElementById('search_input').focus();
vue中 @blur

5.获取input的值
var p = document.getElementById("pwd").value;

  jQuery方法:
	$('body').on('keydown', '#navSearch input', function(e){
		if (e.keyCode == 13) {
			var searchVal = $(this).val();
			if ($.trim(searchVal)=='') {
				layer.msg('请输入您要搜索的内容');
			} else {
				window.location.href = '';
			}
		}
	});

6.居中 css
	方法1：
    margin-left: 50%;
    transform: translateX(-50%);
   -ms-transform:translateX(-50%);     /* IE 9 */
    -moz-transform:translateX(-50%);    /* Firefox */
    -webkit-transform:translateX(-50%); /* Safari 和 Chrome */
    -o-transform:translateX(-50%);  /* Opera */
	
	方法2：
	position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    margin: auto;

7.svn 切分支
    TortoiseSVN---> Switch

8.透明度：
rgba（0,0,0，.5）

opacity: .3;
filter:alpha(Opacity=80);-moz-opacity:0.5;

9.svg图片生成font
https://icomoon.io/app/#/select 生成网站
使用其中的ttf
/*底部图标中更改后的发现图标*/
   @font-face {
    font-family: 'fxicons';
    src: url('../fonts/discover2.ttf') format('truetype');
    font-weight: normal;
    font-style: normal;
}
[class^="ficon-"],
[class*="ficon-"] {
    font-family: 'fxicons';
    speak: none;
    font-style: normal;
    font-weight: normal;
    font-variant: normal;
    text-transform: none;
    line-height: 1;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}
.ficon-font {
    font-size: 19px !important;
}
.ficon-discover:before {
    content: "\e901";
}
.ficon-discover-h:before {
    content: "\e900";

10.接收数据 
get 接收数据
post 传递数据

拼地址：
var info_url = TK.config.SERVER_URL() + "/mlearningapi.php?rt=json";
    var json = {
        "m": "Account/GetLoginCompany",
        "p": {}
    };
    json = JSON.stringify(json);
    var getUrl = info_url +'&p=[' + json + ']';
    TK_Student_Get(info_url,function(data){
        alert(222);
    });
拼接口
var json = [{
        "m": "Cases/GetMyCreateCaseList",
        "p": {
            action: 'getnumber',
            company_id: localStorage.wx_company_id
            }
        }, {
        "m": "Account/GetLoginCompany",
        "p": {}
        }
    }];
    json = JSON.stringify(json);
    var postUrl = '&p=[' + json + ']';
    var url = TK.config.SERVER_URL() + '/mlearningapi.php?rt=json';
    var mycase_num = document.getElementById('mycase_num');
    TK_Student_Post(url, postUrl, function(data, status, xhr) {
        console.log('getnumber==='+JSON.stringify(data));
        if(data.ec == '0') {
            if (isNotEmpty(data.d)) {
                var caseNum = parseInt(data.d[0].count);
                if (caseNum > 0) {
                    mycase_num.innerHTML = caseNum;
                }
            }
        }
    });

11.svn突然被锁住
error: work copy lock
clear up 默认选项即可

12.app版本修改
mainfest.json

13.超出省略怎么处理
css样式：display: -webkit-box;
    	overflow: hidden;
    	white-space: nowrap !important;
    	text-overflow: ellipsis;
   	 word-wrap: break-word;
   	 -webkit-line-clamp: 3;//几行
   	 -webkit-box-orient: vertical;

14.数组添加删除
arr.splice(2,1,"William") 删除&添加
arr.splice(index,howmany,item1,.....,itemX)
index	必需。整数，规定添加/删除项目的位置，使用负数可从数组结尾处规定位置。
howmany	必需。要删除的项目数量。如果设置为 0，则不会删除项目。
item1, ..., itemX	可选。向数组添加的新项目。
arr.push(item1,.....,itemX) 添加
问题：target: [{subject: '111', weight: '111', target_num: '111'},
        {subject: '222', weight: '222', target_num: '22'}]
删除一个object arr.splice(1,1)；
添加一个object let objTrack = {
                        'subject': '',
                        'weight': '',
                        'target_num': ''
                    };
                    vm.trackParm.target.push(objTrack);

15.v-if 和 v-for不能写一起，会相互制约

16.时间戳转换成时间格式
function parseLongToDateByFormat(longDate, formatString) {
	var newDate = new Date();
	newDate.setTime(longDate * 1000);
	return newDate.format(formatString);
}
let beTime = parseLongToDateByFormat(data.data.track.begintime, "yyyy-MM-dd hh:mm")

17.去除数据中的p标签
string.replace(/\<p\>|\<\/p\>/g, '')

18.ios版本低，注意c3最新属性
div{
transform:rotate(7deg);
-ms-transform:rotate(7deg); 	/* IE 9 */
-moz-transform:rotate(7deg); 	/* Firefox */
-webkit-transform:rotate(7deg); /* Safari 和 Chrome */
-o-transform:rotate(7deg); 	/* Opera */
}

19.
微信打开
/front_new/pxb/webapp/html/manager/manager.html#!/track/person&track_id=898

20.关于循环
数组用for(var i=0;i<arr.length;i++){}
对象用for(var s in arr){} s代表对象前的key值


:style="envType === 'webapp'? 'top: 100px;' : 'top: 145px;'"

21.pc端页面刷新
window.location.reload();

22.php htm页面 loop循环
<!--{if $use_scene_arr}-->
	<!--{loop $use_scene_arr $key $value}-->
		<option value ="<!--{$key}-->"><!--{$value['name']}--></option>
	<!--{/loop}-->
<!--{/if}-->

23.select选中的值
jQuery("#useScene").find("option:selected").attr("value");

24.serializeArray方法直接取表单中input和textarea
var data = jQuery('#micro_info').serializeArray();

25.post一般是发出请求  get一般获取数据
var req_url = location.protocol + '//' + location.host + '/Api2/MicroTv/AddContact';
//            var req_url = 'http://test.91pxb.com/Api2/MicroTv/AddContact';（写死请求地址）
            dataJson = JSON.stringify(dataJson);
            if(!clicked) { （提交按钮保护）
                clicked = true;
                jQuery.ajax({
                    type: "POST",
                    url: req_url,
                    data:dataJson,
                    dataType: "json",
                    beforeSend: function () {
                    },
                    success: function (req_result) {
                        layer.showSuccessDialog('已收到您的需求，1－3个工作日内会有专业的直播顾问为您服务！', 2000, function(){
                            window.location.href = location.protocol + '//' + location.host;
                        });
                        clicked = false;
                    },
                    complete:function() {
                        clicked = false;
                    },
                    error:function(){
                        layer.showErrorDialog('请求出错');
                        clicked = false;
                    }
                });
            }

26.vue1.0 v-for(index, item) vue2.0 v-for(item, index)

27.禁止页面视频全屏播放
   <video  webkit-playsinline playsinline id="videoplayer" :src="currentVideoUrl" controls="controls" width="100%" :height="videoHeight" v-show="playVideo" class="package_content" autoplay="autoplay" :poster="currentVideoImg">
                                您的浏览器不支持 video 标签。
            </video>
   webkit-playsinline playsinline 为true 禁止全屏播放

28.视频强制横屏
if (vm.envType === 'app') {
                    mui.back = function () {
                        self.close();
                    };
                    if (mui.os.android) {
                        let self = plus.webview.currentWebview();
                        self.setStyle({
                            videoFullscreen: 'landscape'
                        });
                    } else if (mui.os.ios) {
                        // 监听的事件与Android平台有很大区别
                        let videoElem = document.getElementById('videoplayer');
                        if (videoElem !== null) {
                            videoElem.addEventListener('webkitbeginfullscreen', function () {
                                plus.screen.lockOrientation('landscape'); // 锁死屏幕方向为横屏
                            });
                            videoElem.addEventListener('webkitendfullscreen', function () {
                            //  plus.screen.unlockOrientation(); //解除屏幕方向的锁定，但是不一定是竖屏；
                                plus.screen.lockOrientation('portrait'); // 锁死屏幕方向为竖屏
                            });
                        }
                    }
                }
方法页面：http://ask.dcloud.net.cn/article/1077

29.清除苹果 input标签自带小人
input {
        -webkit-appearance:none!important; /*去除input默认样式*/
    }

30.video标签
<video  
webkit-playsinline 控制webview使用html5的video播放视频不全屏(inline)的方法
playsinline 控制webview使用html5的video播放视频不全屏(inline)的方法
:src="currentVideoUrl"  要播放的视频的 URL。
controls="controls" 如果出现该属性，则向用户显示控件，比如播放按钮。
autoplay="autoplay"  	如果出现该属性，则视频在就绪后马上播放。
:poster="currentVideoImg" 带有预览图（海报图片）的视频播放器：

width="100%" 
:height="videoHeight" 

id="videoplayer" 
class="package_content" 
v-show="playVideo"  vue
>
                                您的浏览器不支持 video 标签。
            </video>

31.清除浮动
<div style="clear: both"></div>

32.居中
div设置了高度和行高 里面包含一个div方块位置偏高
可以设置float:left 并设置margin-top

33.AQLyog-64 bit数据库
现在我们希望从 "Persons" 表中选取所有的列。
请使用符号 * 取代列的名称，就像这样： SELECT * FROM Persons

SELECT * FROM pre_tt_student WHERE root_company_id=625567 AND mobile='18588649989' AND disabled=0
              表单                 公司id                  

34.
plus.storage.setItem('company', JSON.stringify(company));    

35.图片路径处理
TK.config.SERVER_PXB() + '/data/attachment/peixunbao/' + content； 取绝对路径 再拼接地址

36.编码 解码
 encodeURIComponent() 函数可把字符串作为 URI 组件进行编码。
decodeURIComponent 解码

37.
switch 切分支
merge 合并 

38.控制iframe内的视频
let video = document.getElementById('videoplayer');
if (isNotEmpty(video)) {
	video = document.getElementById('RMid').contentWindow.document.getElementById('taoke_video_html5_api');
}

39.判断是微信端还是手机端
envType: HttpUtils.envType(),

export default class HttpUtils {

    static isSwitchToMock () {
        if (mui.os.plus) {
            return false;
        }

        return true;
    }

    static envType () {
        let domain = window.location.host;
        if (domain.indexOf('taoke.com') > 0 || domain.indexOf('taoke.cn') > 0) {
            return 'webapp';
        }

        if (mui.os.plus) {
            return 'app';
        }

        return 'local';
    }
}

40.新建文件夹 然后用svn  svn checkout   url of repository:里写下切的分支

41.this.message = this.message.split('').reverse().join('') 颠倒message
   split() 方法用于把一个字符串分割成字符串数组。 如果把空字符串 ("") 用作 separator，那么 stringObject 中的每个字符之间都会被分割。
   reverse() 方法用于颠倒数组中元素的顺序。
   join() 方法用于把数组中的所有元素转换一个字符串。
   var fruits = ["Banana", "Orange", "Apple", "Mango"];
   var energy = fruits.join(" and ");   ===>     Banana and Orange and Apple and Mango

42.vue1.0 升级vue2.0
vue1.0中 子组件  vm.$dispatch('openFile', attachObj); 传方法 
父组件中接收
events: {
	openFile (msg) {
                this.openCurrentFile(msg);
            }
}

vue2.0 
>>>>关于子父组件传递
没有events
子组件 this.$emit('openFile', attachObj);
父组件
<router-view :course="course"  :attach-list="attachList" :assessment="assessment" :is-scroll="isScroll" :thumb-notnull="commentContent.thumbNotNull"
                         :course-comment="courseComment"  :count="count" :has-support="hasSupportItem" :company-id="data.company_id" :comment-notnull="commentContent.commentNotNull"
                         :course-id="data.course_id" :support-members = "data.supportMembers" :assess-empty = "attachContent.assessEmpty" :attach-download = "attachContent.download"
                         :student-identity = "data.studentIdentity" :attach-empty = "attachContent.attachEmpty" :attach-type-id="attachTypeId" :env-type="envType"
                         :study-empty = "studyIsNull()"
                         @commentParm="commentParm" @thumbParm="thumbParm" @openFile="openFile">
</router-view>

>>>>关于ready() --->改成了  mounted()

43.适应不同屏幕 css
@media  screen and (min-width:1025px){
    html, body{font:16px/1.5 tahoma,arial,'Hiragino Sans GB',\5b8b\4f53,sans-serif;color:#333;margin: 0 auto;}

}
@media  screen and (max-width:1024px) and (min-width:600px){
    html, body{font:16px/1.5 tahoma,arial,'Hiragino Sans GB',\5b8b\4f53,sans-serif;color:#333;}

}

@media  screen and (max-width:599px) and (min-width:400px){
    html, body{font:14px/1.5 tahoma,arial,'Hiragino Sans GB',\5b8b\4f53,sans-serif;color:#333;}

}

44.package.json
 "scripts": {
        "dev": "webpack-dev-server --inline --progress --config vue_last/build/webpack.dev.conf.js",
        "web": "node vue_last/build/build.js --webapp=true",
        "app": "node vue_last/build/build.js",
        "appdev": "node vue_last/build/build.js --appdev=true --watch"
    },

45.因为 v-if 是一个指令，所以必须将它添加到一个元素上。但是如果想切换多个元素呢？此时可以把一个 <template> 元素当做不可见的包裹元素，并在上面使用 v-if。最终的渲染结果将不包含 <template> 元素。

46.获取自身http自带的参数
PlusUtils.getSelfWebView(function (self) {
	type = vm.getType(self);
	vm.sourceOrRule(type);
});
配套js：
export default class HttpUtils { 
	static devLocal () {
        	if (window.location.host && window.location.host.indexOf('localhost') === 0 && window.location.href.indexOf('http://localhost:908') !== 0) {
            		return true;
        	}
        	return false;
    	}
	static envType () {
        	let domain = window.location.host;
        	if (domain.indexOf('taoke.com') > 0 || domain.indexOf('taoke.cn') > 0 || window.location.href.indexOf('http://localhost:908') === 0) {
            		return 'webapp';
        	}

        	if (mui.os.plus) {
            		return 'app';
        	}

        	return 'local';
    	}
	static isFuckWeixinStatistic (url) {
        	if (url.indexOf('from=timeline') || url.indexOf('from=groupmessage') ||
            	url.indexOf('from=singlemessage')) {
            		return true;
        	}
        	if (url.indexOf('isappinstalled=0') || url.indexOf('isappinstalled=1')) {
            		return true;
        	}
        	return false;
    	}
	static filterWeixinStatistic (url) {
        	url = url.slice(0, url.indexOf('student.html') + 12) + url.slice(url.indexOf('#'));
        	return url;
    	}
}

import HttpUtils from './../api/http-utils';
export default class PlusUtils {
	static getSelfWebView (success) {
        	let envType = HttpUtils.envType();
        	if (envType === 'app') {
            		mui.plusReady(function () {
                		let self = plus.webview.currentWebview();
                		success(self);
            		});
        	}

        	if (envType === 'webapp' || HttpUtils.devLocal()) {
            		let paramsObj = PlusUtils.getUrlArgObject();
            		return success(paramsObj);
        	}

        	if (envType === 'local') {
            		return success('');
        	}
    	}
	static getUrlArgObject () {
        	let vars = [], hash;
        	let url = window.location.href;
        	if (HttpUtils.isFuckWeixinStatistic(url)) {
            		url = HttpUtils.filterWeixinStatistic(url);
        	}
        	let hashes = url.slice(url.indexOf('?') + 1).split('&');
        	for (let i = 0; i < hashes.length; i++) {
            		hash = hashes[i].split('=');
            		vars.push(hash[0]);
            		vars[hash[0]] = hash[1];
        	}
    	    	return vars;
    	}
}

47.不为空
function isNotEmpty(obj) {
	if(typeof obj == 'undefined') {
		return false;
	}

	if(obj == null) {
		return false;
	}

	if(obj.toString() == '') {
		return false;
	}

	return true;
}
空对象判断
isEmptyObject: function( obj ) {
	var name;
	for ( name in obj ) {
		return false;
	}
	return true;
}

48.<v-touch tag="div"
                                 class="mui-control-item"
                                 style="font-size: 15px;"
                                 v-on:tap="RankTab('week')"
                                 v-bind:class="[curTAb=='week'?'mui-active':'', '']" >
                            周排名
                        </v-touch>
49.微信分享
判断是否为微信环境
static isWeiXin () {
        let ua = window.navigator.userAgent.toLowerCase();
        let res = ua.match(/MicroMessenger/i);
        if (res !== null && res.toString() === 'micromessenger') {
            return true;
        } else {
            return false;
        }
    }

设置微信分享出去内容
static setJWeiXin (signPackage) {
        console.log(JSON.stringify(signPackage));
        window.weixin_link = signPackage.link;
        window.weixin_send_img = signPackage.send_img;
        window.weixin_send_title = WeiXinLib.strTrim(signPackage.send_title);
        window.weixin_send_desc = WeiXinLib.strTrim(signPackage.send_desc);
    }

50.时间的换算
>>推上一周
var today = new Date();
today.setDate(today.getDate()-7);

给了一个时间戳给我
1515340800 ==> 2018/1/08
var b = new Date(1515340800*1000);
b.setDate(b.getDate()-7);
var c= b.getFullYear()+"/"+(b.getMonth()+1)+"/"+b.getDate();
c  2018/1/1

51.mint ui
http://blog.csdn.net/u010014658/article/details/72912200 demo

初始化下拉刷新 上拉加载
<mt-loadmore :top-method="loadTop" :bottom-method="loadBottom" :bottom-all-loaded="allLoaded" :max-distance="150"
                                     @top-status-change="handleTopChange" ref="loadmore">
</mt-loadmore>

loadTop: function () {  // 刷新数据的操作
	var self = this;
	setTimeout(function () {
                    self.list.splice(0, self.list.length);
                    var i =0, len=20;
                    for (; i< len; i++){
                        self.list.push('demo' + i);
                    }
                    self.$refs.loadmore.onTopLoaded();
          }, 2000);
},
loadBottom: function () { // 加载更多数据的操作
	//load data
	//this.allLoaded = true;// 若数据已全部获取完毕
	var self = this;
	setTimeout(function () {
		var i =0; len = 10;
		for (; i< len; i++){
                        self.list.push('dddd' + i);
		}
		self.$refs.loadmore.onBottomLoaded();
	}, 2000);

}

allLoaded 主要用于判断数据是否加载完毕 默认false

按钮选择
<mt-actionsheet  
            :actions= "actions"  
            v-model="sheetVisible">  
        </mt-actionsheet>

弹框
MessageBox.confirm('事项删除后，将不可恢复。', '确定删除事项？').then(action => {
                    if (action === 'confirm') {
                        let postUrl;
                        let postDate;
                        if (vm.signObj.event_type === 'attended' || vm.signObj.event_type === 'online' || vm.signObj.event_type === 'activity') {
                            
                        }
                        ProjectApi.postItemsDelete(
                            vm.courseId,
                            vm.parseDelete
                        )
                    }
                });

52.点击穿透：
 vue @click.prevent='sendCode' 在click后加.prevent 
 或者 e.preventDefault(); 阻止默认事件

53.在线字体 有字库

54.切图神器：PxCook

55.兼容性强的动画库 animate.css  https://daneden.github.io/animate.css/

56.建立在vue上的ui框架 mint UI vue2.0升级后使用的 iview  vonic

57.页面滚动 wow.js

58.三角形
.triangleDown{
        border-color: #555 transparent transparent transparent;
        border-style: solid;
        border-width: 6px 4px 0 4px;
        height: 0;
        width: 0;
        display: inline-block;
        margin-left: 4px;
    }

59.CSS鼠标响应事件
onMouseDown 按下鼠标时触发 
onMouseOver 鼠标经过时触发 
onMouseUp 按下鼠标松开鼠标时触发 
onMouseOut 鼠标移出时触发 
onMouseMove 鼠标移动时触 

给搜索框 添加阴影
<style type="text/css"> 
.Off{
        cursor: pointer;
        position: relative;
        width: 275px;
        height: 28px;
        background: white;
        line-height: 30px;
        border-radius: 2px;
        padding-top: 7px;
    }
    .Up{
        cursor: pointer;
        position: relative;
        width: 275px;
        height: 28px;
        background: white;
        line-height: 30px;
        border-radius: 2px;
        padding-top: 7px;
        box-shadow:-2px 1px 20px #e5e5e5;
    }
</style> 
</head> 
<body> 
<div class='Off' id="searching" style="position: relative"  onMouseOut="this.className='Off'" onMouseOver="this.className='Up'"></div>
</body> 
</html>

60.select样式修改
去掉 三角形
select{
appearance: none;
    -moz-appearance: none;
    -webkit-appearance: none;
}
select居中
{
 text-align: center;
    text-align-last: center;
}

61.鼠标进入和退出方法 改变样式和控制显示
   $('.index_category > .item').hover(function () {
    
	     $(this).addClass('item_hover');
   
	     $(this).children('.i_bd').show();
   }, function () {
    
	    $(this).removeClass('item_hover');
    
	    $(this).children('.i_bd').hide();

   });

62.es6 查找字符串包含的字符串 返回true or false
	let test = "hello world!";
	test.includes('d',6); //true  后面是第几个开始找
	test.endsWith('hello',5); //从后面开始找
	test.startsWith("w",6);  //从前面开始找 
	可以不包含索引

	// repeat方法返回一个新字符串，表示将原字符串重复n次
	'xx'.repeat(3);
	//后面括号中 小数点取整2.3/2.8都为2 负数或Infinity报错 
	  字符串内不是数字为0处理 字符串有数字转为数字

	// padStart() ; padEnd();
	// ES6引入了字符串补全长度的功能。如果某个字符串不够指定长度，会在头部或尾部补全。
	"x".padStart(5,"ab");  //ababx
	'x'.padEnd(5,"ab");   //xabab
	//上面代码中，padStart和padEnd一共接受两个参数，
	  第一个参数用来指定字符串的最小长度，第二个参数是用来补全的字符串。
	//如果原字符串的长度，等于或大于指定的最小长度，则返回原字符串。

	// 如果省略第二个参数，默认使用空格补全长度。
   	 "x".padStart(5) //"     x"
    	"x".padEnd(4) //"x    "
	//padStart的常见用途是为数值补全指定位数。
   	"1".padStart(10,"0") ; //"0000000001"
	// 另一个用途是提示字符串格式。
    	"12".padStart(10,"YYYY-MM-DD"); // "YYYY-MM-12";
    	"09-12".padStart(10,"YYYY-MM-DD") ; //"YYYY-09-12"

63.图片放大加时间变缓
img{
    -webkit-transform: scale(1.2);
    -moz-transform: scale(1.2);
    -ms-transform: scale(1.2);
    -o-transform: scale(1.2);
    transform: scale(1.2);
    -moz-transition: all 1s ease 0s;
    -o-transition: all 1s ease 0s;
    -webkit-transition: all 1s ease 0s;
    transition: all 1s ease 0s;
}

64.本地看数据
http://du.m.test.taoke.com//mlearningapi.php?p=[{%22m%22:%22Member/PersonInfo%22,%22p%22:{%22pxb_member_id%22:1234}}]

65.iframe 拖动兼容
页面嵌套lframe的问题 ios会不能拖动 android是可以拖动的
解决方法：在iframe外部加一个div 里面加上样式-webkit-overflow-scrolling:touch; overflow: scroll;

66.如果是数组的话 直接等于一个会影响另外一个 用 for循环push进去

67.input只允许上传图片类型文件
<input type="file" name="loadPic" id="loadPic" readonly="readonly" value="" @change="chooseImg($event)" accept="image/*"/>

68.php使用
http://lgh.91pxb.com/?mod=tt-weixin&do=self_join
		          文件名     加载模板名
alt + shift + O 搜索文件名
pd($login_member); 显示数据

$nav_bar[] = array('name' => '设置自助开通', 'link' => $_G['trainingtoolurl'] . '?mod=tt-weixin&do=self_join');
变成
Array
(
    [0] => Array
        (
            [name] => 移动学习
            [link] => http://lgh.91pxb.com/?mod=tt-weixin&do=start_psw
        )

    [1] => Array
        (
            [name] => 设置自助开通
            [link] => http://lgh.91pxb.com/?mod=tt-weixin&do=self_join
        )

)
字符串链接 用 . 拼接代替 +

69.苹果浏览器Safari对JS函数库中newDate()函数中的参数的解析中不支持形如“2020-01-01”形式

苹果浏览器safari对new Date(‘1937-01-01‘)不支持，用.replace(/-/g, "/")函数替换掉中划线即可

70.mint UI checklist自带标题div 要移除
let all = document.querySelectorAll('.mint-checklist');
for (let i = 0; i < all.length; i++) {
	let titleObj = all[i].querySelectorAll('.mint-checklist-title')[0];
	titleObj.parentNode.removeChild(titleObj);
}

71.vue2 对象不更新 
先自定义一个对象
	let obj = data.list;
	let str = '#ABCDEFGHIJKLMNOPQRSTUVWXYZ';
		let strArr = str.split('');
		strArr.forEach(initial => {
		let objSign = obj[initial];
		if (typeof objSign !== 'undefined') {
			let arr = [];
			for (var i = 0; i < objSign.length; i++) {
				arr.push({
                                	label: objSign[i].chinese_name,
                                	value: objSign[i].id
                                });
                                vm.students[objSign[i].id] = objSign[i].chinese_name;
                        }
			vm.$set(vm.list, initial, arr);
		}
	});

72.传递 监听
let inhousecourseDetails = plus.webview.getWebviewById('inhousecourse_details');
if (isNotEmpty(inhousecourseDetails)) {
	mui.fire(inhousecourseDetails, 'updateState', {});
}
window.addEventListener('updateState', function (event) {
	vm.projectDetails();
});

73.上拉加载
window.addEventListener('scroll', function () {
                    let srollHeight = document.documentElement.scrollTop || document.body.scrollTop;
                    let windowHeight = document.documentElement.clientHeight;
                    let totalHeight = srollHeight + windowHeight;
                    let docHeight = document.body.scrollHeight - 20;
                    // console.log('srollHeight==' + srollHeight + '  windowHeight == ' + windowHeight +
                    // 'totalHeight== ' + totalHeight + 'docHeight == ' + docHeight);
                    if (docHeight <= totalHeight && vm.page < vm.total && vm.getStatu) {
                        vm.getStatu = false;
                        vm.isScroll = true;
                        vm.page = vm.page + 1;
                        IntegrateApi.getIntegrateDetail([
                            IntegrateApi.getRankingList(
                                vm.type,
                                vm.page,
                                vm.selectBegintime,
                                vm.selectEndtime,
                                vm.parseData
                            )
                        ]);
                    } else if (vm.page >= vm.total) {
                        vm.isScroll = false;
                    }
                });

74.针对不同浏览器
-ms-transform:rotate(7deg);                //-ms代表ie内核识别码
-moz-transform:rotate(7deg);             //-moz代表火狐内核识别码
-webkit-transform:rotate(7deg);         //-webkit代表谷歌内核识别码
-o-transform:rotate(7deg);               //-o代表欧朋【opera】内核识别码

75.只能输入正整数 火狐不兼容type=“number”
<input type="text" name="update_grades[rank]"  pattern="[0-9]\d*"  value="{$level[rank]}" oninput="this.value=this.value.replace(/[^0-9]/g,'');"style="text-align: center;width: 150px;">

76.数组去重
1.计数
var a = [0,2,3,4，4，0,2]；
var obj = {};
var arr = [];
for（var n = 0;n<a.length;n++）{
	(!obj(a[n])){ //如果obj没有相对应的key
		obj（a[n]）= 1;
		arr.push(a[n]);
	}
}
2.indexOf
var a = [0,2,3,4，4，0,2]；
var arr = [];
for(var i = 0; i < a.length; i++) {
	if (arr.indexOf(a[i])<0){
		arr.push(a[i]);
	}
}

77.图片保存 jQuery
H5 canvas

78.div文字底部 display:table  display:table-cell
<div class="main_content">
        <div style="height: 200px;background: #dfdfdd;padding: 10px 30px;box-sizing: border-box;">
            <div class="fl_l" style="height: 45px;display: table;">
                <span style="display: table-cell;vertical-align: bottom;">姓名：<span>阿輝</span></span>
                <span  class="" style="display: table-cell;vertical-align: bottom;padding-left: 50px">工号：<span>21983</span></span>
            </div>
            <span  class="fl_r mar_l_50">最多可获积分<span class="font_big" style="margin-left: 10px">172</span></span>
            <span class="fl_r" style="">已获得积分<span class="font_big" style="margin-left: 10px">225</span></span>
        </div>
    </div>

79.箭头
/ 下箭头
.down-arrow {
    display :inline-block;
    position: relative;
    width: 40rpx;
    height: 30rpx;
    margin-right: 20rpx;
}

.down-arrow::after {
    display: inline-block;
    content: " ";
    height: 18rpx;
    width: 18rpx;
    border-width: 0 2rpx 2rpx 0;
    border-color: #999999;
    border-style: solid;
    transform: matrix(0.71, 0.71, -0.71, 0.71, 0, 0);
    transform-origin: center;
    transition: transform .3s;
    position: absolute;
    top: 50%;
    right: 10rpx;
    margin-top: -10rpx;
}
// 加上active旋转成 上箭头
.down-arrow.active::after {
    transform-origin: center;
    transform: rotate(-135deg);
    transition: transform .3s;
}

80.显示隐藏
jQuery('.eventType > .item').hover(function () {
                            
	jQuery(this).children('.i_bd').show();
                        
}, function () {
                            
	jQuery(this).children('.i_bd').hide();
                        
});

81.php 绑定数据
<!--{if $list}-->
        <!--{loop $list $key $value}-->
            <div class="content_div" {if $value['icon']} style="background: url('/data/attachment/peixunbao/{$value['icon']}?{VERHASH}') 0 no-repeat;background-size: 100% 150px;"{/if}>
                <!--<div class="dis_in_line img_div" style=""></div>-->
                <div class="title_div" style="">
                    <h3 class="ellipsis"><!--{$value['subject']}--></h3>
                    <p  class="ellipsis"><!--{$value['intro']}-->....</p>
                </div>
                <div class="more_cotorl" style="">
                    <div class="dis_in_line">编辑</div>
                    <div class="dis_in_line">更多</div>
                </div>
            </div>
        <!--{/loop}-->
    <!--{/if}-->

82.配置：svn
SVN checkout：https://svn:8443/svn/PXB_src/branches/2018-06-05_bug_fix 分支

83.全选
// 选择全部
    function allCheck(obj){
        if (obj.checked) {
            jQuery('input[name="check"]').prop('checked','true');
        } else {
            jQuery('input[name="check"]').attr('checked',false);
        }
    }

84.html 中 onclick=del();可以直接 onclick=del(this); 指向本身
function chooseLevel(id,t, obj) {
        var cObj = jQuery(obj);
        if (t == 'level') {
            tab_level_id = id;
        } else if (t == 'status') {
            tab_level_status_id = id;
        }
        var data = 'search=' + searchSpan + '&breakthrough_id=' + breakThroughId + '&learning_status=' + tab_level_status_id + '&level_id=' + tab_level_id;
        ajaxPostData(mod, mod_todo, course_id, 'filter', data, filtersuccess);
        return false;
    }

85.关于class添加和移除
function chooseLevel(id, t, obj) {
        if (t == 'status') {
            var events = jQuery('.statusS>.type_choose');
            tab_level_status_id = id;
        } else if (t == 'level') {
            var events = jQuery('.levelS>.type_choose');
            tab_level_id = id;
        }
        for (var i = 0; i < events.length; i++) {
            if (jQuery(events[i]).hasClass('active')) {
                console.log(events[i]);
                jQuery(events[i]).removeClass('active');
            }
        }
        var cObj = jQuery(obj);
        cObj.addClass('active');
        var data = 'search=' + searchSpan + '&breakthrough_id=' + breakThroughId + '&learning_status=' + tab_level_status_id + '&level_id=' + tab_level_id;
        ajaxPostData(mod, mod_todo, course_id, 'filter', data, filtersuccess);
        return false;
    }

86.阻止冒泡事件
1.event.stopPropagation()方法

这是阻止事件的冒泡方法，不让事件向documen上蔓延，但是默认事件任然会执行，当你掉用这个方法的时候，如果点击一个连接，这个连接仍然会被打开，

2.event.preventDefault()方法

这是阻止默认事件的方法，调用此方法是，连接不会被打开，但是会发生冒泡，冒泡会传递到上一层的父元素；

3.return false  ；

这个方法比较暴力，他会同事阻止事件冒泡也会阻止默认事件；写上此代码，连接不会被打开，事件也不会传递到上一层的父元素；可以理解为return false就等于同时调用了event.stopPropagation()和event.preventDefault()

87.php 渲染页面 计算
<div class="bor_content">
                        <!--{if $level['events']}-->
                            <!--{loop $level['events'] $k $event}-->
                                <div class="te_cotent {if $event['status']==0}unstudy{/if}">
                                    {eval $number = $k+1}
                                    <span style="width:10.5%;"><!--{$number}--></span>
                                    <span style="width: 42%;">
                                        <!--{if $event['event_type']=='exam'}-->
                                        [考试]
                                        <!--{else}-->
                                            <!--{if $event['is_required']==1}-->
                                            [必修 课程]
                                            <!--{else}-->
                                            [选修 课程]
                                            <!--{/if}-->
                                        <!--{/if}-->
                                        <!--{$event['subject']}-->
                                    </span>
                                    <span style="width: 15.7%;height: 50px">
                                    <!--{if  $event['status']!=0}-->
                                        <!--{if $event['event_type']=='exam'}-->
                                        通过()
                                        <!--{else}-->
                                        已学
                                        <!--{/if}-->
                                    <!--{/if}-->
                                    </span>
                                    <span style="width: 15.7%;"><!--{$event['point']}--></span>
                                    <span class="ess_hid" style="width: 15.7%;"><!--{eval echo date('Y/m/d H:i', $level['breakthrough_endtime'])}--></span>
                                </div>
                            <!--{/loop}-->
                        <!--{/if}-->
                    </div>

88.php 时间戳转换
<!--{eval echo date('Y/m/d H:i', $level['breakthrough_endtime'])}-->

89.js 字母倒排
var a = 'hello';
var b = a.split(''); // b (5)?["h", "e", "l", "l", "o"]
var c = b.reverse(); // c (5)?["o", "l", "l", "e", "h"]
var d = c.join(''); // d "olleh"

89.
/**
 * 监听页面可见变化
 * @param changefunction 变化执行的函数
 */
function listenPageVisibilityChange(changefunction) {
    //网页当前状态判断
    var hidden, state, visibilityChange;
    if (typeof document.hidden !== "undefined") {
        hidden = "hidden";
        visibilityChange = "visibilitychange";
        state = "visibilityState";
    } else if (typeof document.mozHidden !== "undefined") {
        hidden = "mozHidden";
        visibilityChange = "mozvisibilitychange";
        state = "mozVisibilityState";
    } else if (typeof document.msHidden !== "undefined") {
        hidden = "msHidden";
        visibilityChange = "msvisibilitychange";
        state = "msVisibilityState";
    } else if (typeof document.webkitHidden !== "undefined") {
        hidden = "webkitHidden";
        visibilityChange = "webkitvisibilitychange";
        state = "webkitVisibilityState";
    }
    // 添加监听器，在title里显示状态变化
    document.addEventListener(visibilityChange, function() {
        // document.title = document[state];
        changefunction();
    }, false);
}
