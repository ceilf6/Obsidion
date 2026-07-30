# Model Service

API形式

HTTP请求

OpenAI 

SDK

已经帮忙封装了请求了

支持所有兼容了 OpenAI 的格式的大模型，像 Kimi 等

所有模型服务提供商都支持的

# 核心

用户消息-自然语言 → 

前处理 → 自回归 → 后处理 

→ 回复-自然语言

## 前处理

身份、权限认证 - API Key

提示词注入

拼接进入 system 系统提示词：你是阿里的千问大模型

分词、Token化 Tokenization

## 自回归

调用裸模型

```jsx
const input = []

while(1){
	const GaiLv = raw_model(input)
	
	const token = pickToken(GaiLv, options)
	
	if(isOverToken(token)){
		break
	}
	
	output.push(token)
	
	input.push(token)
}
```

回归调用

这也就是为什么 输入的token便宜，输出的token贵 ，因为最后输出的前面已经拼接了很多内容

输出的数量 = 回归的次数

### options

其中 用户的配置 会影响 pickToken

- temperature
    
    概率分布
    

进行截断

- top_k
    
    数量，按概率从高到低
    
- top_p
    
    核采样，按概率来取
    
    0.8 累加到 80% 就不取了
    

## 后处理

Detokenization

将 Token → 自然语言

合规性检查