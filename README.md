# php_light_agent
## 简单的php轻量级内网浏览代理
* 这是一个使用php写的简单的内网浏览代理，可以直接通过控制请求参数将内网内容展现到页面上（包括js、css都可以加载）
## 使用方法
* 请求参数介绍
  * $_REQUEST['url'] -> 代理目标
  * $_REQUEST['method'] -> 首次请求所使用的请求方法
  * $_REQUEST['rmethod'] -> 遇到跳转时所使用的请求方法
  * $_REQUEST['data'] -> POST请求参数
  * $_REQUEST['params'] -> GET请求参数
  * $_REQUEST['cookie'] -> 请求时所附带的COOKIE值
  * $_REQUEST['headers'] -> 请求时自定义的请求标头
  * $_REQUEST['type'] -> 请求方式（有4种，前3种分别对应 socket file_get_contents curl 的内网代理，最后1种是单纯的file_get_contents()，可以玩php伪协议）
* 配置参数
  * $REDIRECT_AUTO -> 是否自动跳转
  * $REDIRECT_COOKIE_USE -> 跳转时是否使用cookie
  * $TIMEOUT -> 请求超时时间
## 简单例子
 * url=http://10.10.16.3/index.html&method=post&remethod=get&data=a=123%26b=321&params=c=123&headers[0]=user-agent:dqv5
  * 内网目标页面 -> http://10.10.16.3/
  * 首次访问方法 -> POST
  * 若遇到跳转则使用的请求方法 -> GET
  * POST请求参数 -> a=123&b=321
  * GET请求参数 -> c=123
  * 额外请求标头 -> user-agent : dqv5
