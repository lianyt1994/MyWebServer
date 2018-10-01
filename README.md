# MyWebServer
<br>
手写web服务器工作流程：<br>
    1、jvm加载时先加载web.xml，经过WebApp解析后，把每个url对应的servlet的名称存成静态map。<br>
    2、server启动后开启serverSocket，while(true)循环accept，每收到一个请求，就新建一个dispatch线程去处理得到的socket，继续accept。<br>
    3、dispatch传入得到的socket，在构造函数里先new request，new response，request，response 的构造函数里获得socket的InputStream和OutputStream，用来获取传过来的数据和传回去的数据。<br>
    4、request的构造函数里面解析request后得到url，然后从WebApp中之前从web.xml中解析得到的url找到对应的servlet，new出来来处理这个请求，然后通过response把响应回传，终止socket，完成请求响应过程。
