# Node.js 定时任务的实现。

有时候需要服务器可以定时做一些任务，例如写日报之类。实现定时任务的方法很多种，可以利用第三方模块例如later等。
这里介绍一个简单的实现，有空的朋友可以封装为一个模块。

```js
/**每天0点的时候做任务*/

//定义常量
const ONE_DAY = 24*60*60*1000;//one day.一天。

var startCronjob = function(){
	//计算距离第二天0点的时间
	var timegap = date_util.getToday()*1000 + ONE_DAY - date_util.getNowTimestamp()*1000;
	setTimeout(function(){
		doJobEveryday();
	},timegap);
}

var doJobEveryday = function(){
	
	doSomeJob();
	
	//and then do it every day
	setTimeout(function(){
		doSomeJob();
	},ONE_DAY);

}

var doSomeJob = function(){
	//do your job 
	//the job code
	//.....
}

//final,just startCronjob(),it will doSomeJob everyday.
startCronjob();

```