## ngx_http_log_module

Based on the nginx stable 1.8.0，You can direct the `src/http/modules/ngx_http_log_module.c` file cover, also can make a `patch`.


```
Syntax:
access_log path [format [buffer=size [flush=time]] [if=condition] [sample=percentage:status,status]];

```

example:
```
sample=50%:200,404
Desc: The status code is 200, 404, the sampling output of 50%。

```

基于nginx最新稳定版1.8.0的日志模块做了修改。增加了参数，支持日志采样输出。你可以直接把`src/http/modules/ngx_http_log_module.c` 文件覆盖掉，也可以打个`patch`。


```
access_log path [format [buffer=size [flush=time]] [if=condition] [sample=percentage:status,status]];

```

举例说明：
编译好版本以后，在access_log的配置后添加`sample=50%:200,404`,就会对状态码是200的和404的采样输出50％。

如果需要根据其他条件采样输出，也可基于本代码再次修改。例如：
sample=50%$status:200,404


