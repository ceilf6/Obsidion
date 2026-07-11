# 内部Skill适配codex

Source: [KM 2754701987](https://km.sankuai.com/collabpage/2754701987)

## 背景

想在 codex 中访问内网资料

但是 Friday skills 技能广场上下载下来默认都是存在 .claude/skill 里面也就是说只能是 cc亲属 才配使用

[image.png](https://km.sankuai.com/api/file/cdn/2754701987/230180176342?contentType=1&isNewContent=false)

[image.png](https://km.sankuai.com/api/file/cdn/2754701987/230179520787?contentType=1&isNewContent=false)

## 实践

直接将 .claude/skills 复制到 .codex/skills

> **ℹ️ 信息：**
> 
> 
> 像如果从 .codex/skills 复制到 .claude/skills 还需要在 .claude/.mtskills-source.jsonl 中记录该技能相关的信息
> 

[image.png](https://km.sankuai.com/api/file/cdn/2754701987/230183802489?contentType=1&isNewContent=false)

## 踩坑

过程中需要提供 MIS号 然后大象点击认证

但是大模型经常遇到问题后不及时反馈导致信息源错误，所以可以结合 PUA 这个 SKILL “压榨”大模型能力

[image.png](https://km.sankuai.com/api/file/cdn/2754701987/230189100645?contentType=1&isNewContent=false)