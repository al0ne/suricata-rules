### Linux wget/curl download .sh script
    一些恶意软件使用curl或者wget下载sh脚本执行，常见于挖矿木马。

### Windows Powershell Request UserAgent
    匹配powershell web cmdlet user-agent特征

### Hacker backdoor or shell  Microsoft Corporation
    TCP流量中匹配windows cmd启动后回显信息“Microsoft Corporation”，常见场景nc反弹，添加depth修饰符只在前200字节匹配避免误报。
    Microsoft Windows [版本 6.1.7601]
    版权所有 (c) 2009 Microsoft Corporation。保留所有权利。
    
### Hacker backdoor or shell Microsoft Windows
    同上 匹配“Microsoft Windows [”关键字 

### 可疑的netstat命令流量
    HTTP中匹配cmd执行netstat响应结果，常见于命令执行。

### http GET data
    HTTP协议中GET请求也可以像POST那样在请求体中传输数据，大多数IDS以及协议还原设备对于GET请求这块是只记录URL，
    如果传输数据在流量还原中只会当成在正常的访问请求，SSR中http混淆就是使用这种方法。
    47 45 54 匹配HTTP GET关键字，0d0a0d0a是HTTP协议分隔符，wireshark追踪流后发现0d0a0d0a就是请求体结尾，后面跟着响应数据，
    此条规则匹配0d0a0d0a后面还有数据的情况，并且排除掉了一些正常业务（排除掉{和<字符串）。
    
### Mining_Behavior_Detection
    检测流量中使用stratum协议的挖矿行为。
