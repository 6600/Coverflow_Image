

|      属性     |     含义      |      初始值     |    重要性      |
| ------------- |:-------------:| ------------- |:-------------:|
| id     |元素的id |  无     |必须 | 



##1.静态添加：
```javascript
    <div id="shelf" style="background-position:0 0;"> 
        <div id="container2"> 
            <img title="title #1" src="images/1.jpg" /> 
            <img title="title #2" src="images/2.jpg" /> 
            <img title="title #3" src="images/3.jpg" /> 
            <img title="title #5" src="images/5.jpg" /> 
            <img title="title #6" src="images/6.jpg" /> 
            <img title="title #7" src="images/7.jpg" /> 
            <img title="title #1" src="images/1.jpg" /> 
            <img title="title #2" src="images/2.jpg" /> 
            <img title="title #3" src="images/3.jpg" /> 
            <img title="title #4" src="images/4.jpg" /> 
        </div> 
   </div> 
   <script type="text/javascript">
        $(function(){
        	$('#container2').coverscroll();
	    });
	</script> 
```
##效果演示：
![mahua](http://myweb-10017157.file.myqcloud.com/gif/131171301758023398.gif)

##2.动态添加
```javascript
<div id="shelf"> 
    <div id="container"> 
     <div class="item"> 
      <img src="images/1.jpg" /> 
      <div class="similarity">05</div> 
      <div class="itemTitle">the title 1</div> 
     </div> 
    </div> 
   </div>
   <!--shelf end--> 
   <script type="text/javascript">
    $(function(){
		$('#container').coverscroll({
			items:'.item',
			minfactor:10,
			scalethreshold:5,
			staticbelowthreshold:true,
			distribution:1
		});
	});

	// 演示，动态地添加项目的CoverScroll
	var cnt = 0;
	var aitems = [
		'<div class="item"><img  src="images/2.jpg" /><div class="similarity">05</div><div class="itemTitle">the title 2</div></div>',
		'<div class="item"><img  src="images/3.jpg" /><div class="similarity">05</div><div class="itemTitle">the title 3</div></div>',
		'<div class="item"><img  src="images/4.jpg" /><div class="similarity">05</div><div class="itemTitle">the title 4</div></div>',
		'<div class="item"><img  src="images/5.jpg" /><div class="similarity">05</div><div class="itemTitle">the title 5</div></div>',
		'<div class="item"><img  src="images/6.jpg" /><div class="similarity">05</div><div class="itemTitle">the title 6</div></div>',
		'<div class="item"><img  src="images/7.jpg" /><div class="similarity">05</div><div class="itemTitle">the title 7</div></div>',
		'<div class="item"><img " src="images/1.jpg" /><div class="similarity">05</div><div class="itemTitle">the title 8</div></div>',
		'<div class="item"><img " src="images/2.jpg" /><div class="similarity">05</div><div class="itemTitle">the title 9</div></div>',
		'<div class="item"><img " src="images/3.jpg" /><div class="similarity">05</div><div class="itemTitle">the title 10</div></div>',
		'<div class="item"><img " src="images/4.jpg" /><div class="similarity">05</div><div class="itemTitle">the title 11</div></div>',
		'<div class="item"><img " src="images/5.jpg" /><div class="similarity">05</div><div class="itemTitle">the title 12</div></div>',
		'<div class="item"><img " src="images/6.jpg" /><div class="similarity">05</div><div class="itemTitle">the title 13</div></div>',
		'<div class="item"><img " src="images/7.jpg" /><div class="similarity">05</div><div class="itemTitle">the title 14</div></div>'
	];

	function addItem(){
		$('#container').append(aitems[cnt]);
		$('#container').coverscroll({
			items:'.item',
			minfactor:10,
			scalethreshold:5,
			staticbelowthreshold:true,
			distribution:1,
			bendamount:1.5,
			movecallback:getStatus
		});
		cnt++;
		if(cnt >= aitems.length){
			cnt=0
		}
	}
	function getStatus(){
		var stats = ($('#container .selectedItem').index()+1)+' of '+$('#container .item').length;
		$('#stats').html(stats);
	}
	</script> 
```
##效果演示：
![mahua](http://myweb-10017157.file.myqcloud.com/gif/131171302799922775.gif)
