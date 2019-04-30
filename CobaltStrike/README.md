### CobaltStrike login server
    cobaltstrike客户端与团队服务端通讯走ssl，默认证书配置在teamserver文件中
    keytool -keystore ./cobaltstrike.store -storepass 123456 -keypass 123456 -genkey -keyalg RSA -alias cobaltstrike -dname "CN=google.com OU=xsser, O=xsser, L=Somewhere, S=Cyberspace, C=Earth"

### CobaltStrike download.windowsupdate.com C2 Profile
    正常windows更新域名，uri是十六进制形式，日期变动，格式固定。cobaltstrike c2通过更改host伪造windows更新产生的流量，将传输的
    数据base64后放到url中，例如：
    GET /c/msdownload/update/others/2016/12/29136388_oY_bIWScNUZ3X5ebOUqkFA.cab HTTP/1.1
    Accept: */*
    Host: download.windowsupdate.com
    User-Agent: Windows-Update-Agent/10.0.10011.16384 Client-Protocol/1.40
    windows更新正常格式“/c/msdownload/update/others/2012/02/8位数字_40位十六进制.cab”

### CobaltStrike HTTP beacon response
    提取cobaltstrike http上线心跳包响应特征
