[English](./README.md) | 简体中文
# suricata-rules
	Suricata是一个优秀的开源入侵检测系统，此项目记录安全运营人员提取的高质量Suricata IDS规则,欢迎大家提交。 

### 规则编写要求如下
每个规则对应新建目录如下

	webshell检测	#规则目录名称-按照对应检测规则描述清楚即可
	- webshell.pcap	#规则对应的pcap包，尽量以flow的形式保存
	- websehll.rules	#自己提取的规则文件，尽量测试过提交。
	- README	#可以描述一些规则相关的东西，便于他人理解，支持Markdown

#### 规则目录
	目录以单个CVE，黑客工具，威胁类型来命名，如果有对应规则目录，建议存放至已有规则目录中。

#### 规则对应pcap包
	规则对应的pcap通过Wireshark筛选后，利用菜单文件--保存特定分组--选择pcap格式上传。
	便于识别恶意流数据，也是最小的，便于移动和备份

#### 规则.rules
	规则文件命名随意，但后缀必须为rules，如：webshell_caidao.rules
	文件中可以出现多个规则文件，README备注中写明
规则内容建议如下：
##### 示例
	sid类型：
	0~1000000   Sourcefire VRT 保留
	2000001~2999999     EMerging Threats(ET)
	3000000~3999999     公用
	网络扫描    3000000～3000999
	暴力破解    3001000～3001999
	漏洞利用    3002000～3002999
	后门链接    3003000～3003999
	WebShell    3004000～3004999
	病毒木马    3005000～3005999
	间谍软件    3006000～3006999
	安全认证    3007000～3007999
	代码执行    3008000～3008999
	文件还原    3009000～3009999
	文件传输    3010000～3010999
	可疑DNS     3011000～3011999
	HTTP请求    3012000～3012999
	恶意行为    3013000～3013999
	违规操作    3014000～3014999
	敏感信息泄漏    3015000～3015999
	黑客工具    3016000～3016999
	rev为规则版本每次修改递增，metadata添加创建日期与创建人
	reference为引用来源/参考资料，例如某CVE编号，或者修复方案，攻击说明等。
	alert http any any -> any any (msg:"webshell_caidao_php"; flow:established; content:"POST";
    http_method; content:".php"; http_uri; content:"base64_decode"; http_client_body;  sid:3004001; 
    rev:1; metadata:created_at 2018_11_14, by al0ne;)

# 注
本项目根目录文件说明

	suricata-ids.rules	#所有规则的集合，更新时直接下载规则文件替换。
	disable.conf	#分析过程中记录Suricata禁用规则(无效、误报等情况)
	sid.txt 	#记录了所有规则的sid 避免重复，每次添加规则后必须更新sid.txt文件。
