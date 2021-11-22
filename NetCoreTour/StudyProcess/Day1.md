### 创建Asp.net core web api 工程，工程名为NetCoreTour.

### 项目添加引用swagger包：

​		引用swagger 包。（swagger解释：Swagger 是一个用于生成、描述和调用 RESTful 接口的 Web 服务）

​		Management GUN Package ，引用：Swashbuckle.AspNetCore包。

### 添加服务。

​	在Startup类的ConfigureServices方法里面注入服务

```c#
	// 添加Swagger
	services.AddSwaggerGen(c =>
	{
		c.SwaggerDoc("v1", new OpenApiInfo { Title = "API Demo", Version = "v1" });
	});
```



### 添加中间件.

​	在Startup类的Configure方法里面添加Swagger有关的中间件：
​	

```c#
if (env.IsDevelopment())
	{
		app.UseDeveloperExceptionPage();
	}
	// 添加Swagger有关中间件
app.UseSwagger();
	app.UseSwaggerUI(c =>
	{
		c.SwaggerEndpoint("/swagger/v1/swagger.json", "API Demo v1");
	});
	app.UseRouting();
```

### 添加控制器

​	Controllers 文件夹中添加controller，里面添加增删改查的方法。

​	运行输入网址：https://localhost:44357/api/Demo

```c#
using Microsoft.AspNetCore.Http;
using Microsoft.AspNetCore.Mvc;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;

namespace NetCoreTour.Controllers
{
    [Route("api/[controller]")]
    [ApiController]
    public class DemoController : ControllerBase
    {
        [HttpGet]
        public string Get()
        {
            return "Tom";
        }

        [HttpPost]
        public void Post()
        {

        }

        [HttpPut]
        public void Put()
        {

        }

        [HttpDelete]
        public void Delete()
        {

        }
    }
}

```



​	









​	