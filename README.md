# xia SQL (瞎注)

> 本插件仅只插入单引号，没有其他盲注啥的，且返回的结果需要人工介入去判断是否存在注入，如果需要所有注入都测试，请把burp的流量转发到xray。

* burp 插件。
* 在每个参数后面填加一个单引号，两个单引号,如果值为纯数字则多加一个-1、-0。
* 由于不会java，且又是用java写的，代码太烂，就不开源了。`（本来是不打算开源的，但是可能还是有人需要自定义一下，那就开源吧）`

***********

## 插件使用描述
* 返回 `✔️` 代表两个单引号的长度和一个单引号的长度不一致，`表明可能存在注入`。
* 返回 `✔️ ==> ？` 代表着 原始包的长度和两个单引号的长度相同且和一个单引号的长度不同，`表明很可能是注入`。
* 支持json格式，暂不支持json多层嵌套。
* 支持参数的值是纯数字则-1，-0。
* 监控Proxy 为被动扫描模式，`优先返回响应包`，后台再发送payload。
* 监控Repeater 为主动扫描模式，`优先发送payload`，待发送完payload后再返回响应包（V1.8以上版本已优化）。
* 同个数据包只扫描一次，算法：`MD5(不带参数的url+参数名+POST/GET)`。
* 支持右键发送到插件扫描（哪怕之前扫描过的，仍然可以通过右键发送再次扫描）。

**********
### 2022-4-11
#### xia SQL 1.9
* 支持json多层嵌套
![image](https://user-images.githubusercontent.com/30351807/162653146-5caaf300-3b1c-4680-af06-e84364a5e3b4.png)


**********
### 2022-4-8
#### xia SQL 1.8
* 新增右键发送到插件扫描
* 优化 监控Repeater 模式下数据包返回速度。
![image](https://user-images.githubusercontent.com/30351807/162444663-ecc491e2-9a74-4d0f-8b1f-c6ce8f61546a.png)


**********
### 2022-4-2
#### xia SQL 1.7
* 修复在burp2.x版本下poxry模式展示内容bug
![image](https://user-images.githubusercontent.com/30351807/161375553-cee2df69-5681-4818-95ae-0ed389795ea4.png)


**********
### 2022-3-31
#### xia SQL 1.6
* 更新相同数据包只扫描一次的算法，算法：MD5(不带参数的url+参数名+POST/GET)
![image](https://user-images.githubusercontent.com/30351807/161045937-d0e3584a-d610-4b26-ba33-6cc08dd9e8fa.png)


**********
### 2022-3-29
#### xia SQL 1.5
* 取消默认选中“监控Repeater”，增加默认选中“值是数字则进行-1、-0”。
* 变更 监控Proxy模式 为被动模式，提升交互体验感。
* 新增相同数据包只扫描一次。算法：MD5(url+参数名)，如果是post包，值变化也不会重新扫描，需要参数名变化才会再次扫描。


**********
### 2022-2-13
#### xia SQL 1.4
* 更新了 一个选项，如果值是纯数字的话就进行-1，-0
![image](https://user-images.githubusercontent.com/30351807/153725862-8ec9e92f-66b5-4d5c-9c3e-fb18f5afaa94.png)


**********
### 2022-2-11
#### xia SQL 1.3
* 更新了 原始包的长度和两个单引号的长度相同且和一个单引号的长度不同就返回 ✔️ ==> ？

![image](https://user-images.githubusercontent.com/30351807/153590052-42293c4a-7a85-4740-b29e-209a7c27d403.png)


**********
### 2022-2-11
#### xia SQL 1.2
* 更新支持json格式

![image](https://user-images.githubusercontent.com/30351807/153567877-479a0e15-9d6c-43f5-84d9-80c5dfb6fd03.png)


**********
### 2022-2-10
#### xia SQL 1.1
* 更新了序列号
* 更新了有变化 打勾
* 更新了如果那个数据包没有参数，那就忽略。这样开 proxy 模式 就不会一堆包了。

![image](https://user-images.githubusercontent.com/30351807/153390045-2b3769f6-151b-45c0-a555-53cda4fef2f2.png)


**********
# 图片展示

![image](https://user-images.githubusercontent.com/30351807/153139897-08e6b69b-f129-4fab-a62e-037351d7c60f.png)

![image](https://user-images.githubusercontent.com/30351807/153139950-a4f51f4b-e39d-459d-91b8-e326c2c74c29.png)


![image](https://user-images.githubusercontent.com/30351807/153139522-b9af5d35-36a3-4204-b2f4-7b6a11253d41.png)
