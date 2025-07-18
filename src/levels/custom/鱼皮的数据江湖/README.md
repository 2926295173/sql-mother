# 鱼皮的数据江湖

## 背景故事
程序员鱼皮是一位技术博主，他在各个平台都有发布内容。最近他发现自己的流量忽高忽低，摸不着头脑。作为他的数据分析助手，你需要帮他找出流量密码，看看到底什么内容最受粉丝欢迎！

## 数据说明
我们有一个内容发布表 `content_posts`，记录了鱼皮在各平台的发布情况：

- `post_id`：内容ID
- `title`：内容标题
- `platform`：发布平台（哔哩哔哩、公众号、知乎、CSDN）
- `content_type`：内容类型（教程、项目分享、技术解析、经验分享）
- `publish_date`：发布日期
- `views`：浏览量
- `likes`：点赞数
- `comments`：评论数
- `duration_minutes`：内容时长（分钟，视频类内容）

## 任务要求
鱼皮想要了解他的创作数据表现，请你编写SQL查询：

1. 计算每个平台每种内容类型的平均互动率（互动率 = (likes + comments) / views * 100）
2. 只显示浏览量大于1000的内容
3. 按平台和互动率排序（平台升序，互动率降序）
4. 返回字段：平台（platform）、内容类型（content_type）、平均互动率（avg_engagement_rate，保留2位小数）、内容数量（content_count）

## 提示
- 使用 ROUND 函数保留小数位数
- 使用 HAVING 子句过滤聚合结果
- 注意处理除零的情况

让我们看看哪个平台的哪种内容最能引起用户互动吧！🚀 