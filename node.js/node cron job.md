# Node.js ��ʱ�����ʵ�֡�

��ʱ����Ҫ���������Զ�ʱ��һЩ��������д�ձ�֮�ࡣʵ�ֶ�ʱ����ķ����ܶ��֣��������õ�����ģ������later�ȡ�
�������һ���򵥵�ʵ�֣��пյ����ѿ��Է�װΪһ��ģ�顣

```js
/**ÿ��0���ʱ��������*/

//���峣��
const ONE_DAY = 24*60*60*1000;//one day.һ�졣

var startCronjob = function(){
	//�������ڶ���0���ʱ��
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

> date_util

```js
	
	 /**��ȡ��������ʱ���*/
    var getToday = function(){
        var today = new Date();
        today.setHours(0);
        today.setMinutes(0);
        today.setSeconds(0);
        today.setMilliseconds(0);
        return Math.floor(today.getTime()/1000);
    }
	
    /**��ȡ����µĵ�һ��ʱ���*/
    var getThisMonth = function(){
        var today = new Date();
        today.setDate(0);
        today.setHours(0);
        today.setMinutes(0);
        today.setSeconds(0);
        today.setMilliseconds(0);
        return Math.floor(today.getTime()/1000);
    },
    /**��ȡʵʱʱ���*/
    var getNowTimestamp = function(){
        return Math.floor(new Date().getTime()/1000);
    }

```