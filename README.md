# peliftA2(fn,p1,p2)
lifeA2 function for Promise and Either

用函数式编程解决常见异步任务

### 函数签名
`peliftA2(fn,p1,p2)`

fn是一个两参数函数  
p1,p2是Promise,返回结果是fn的实参  

### 优点
在p1或p2返回错误时，fn会被自动短路，不执行


### example
		var p1=new Promise(function(ful,rej){
			setTimeout(ful,1000,"p1");
		});
		var p2=new Promise(function(ful,rej){
			setTimeout(ful,2000,"p2");
		});
		var p3=new Promise(function(ful,rej){
			setTimeout(rej,600,"p3 rej");
		});

		function renderPage(p1,p2) {
			console.log(p1,p2)
			return "render ok"
		}


		peliftA2(renderPage,p1,p2); //renderPage run
		peliftA2(renderPage,p1,p3); //renderPage not run because p3 reject
