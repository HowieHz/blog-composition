# blog-composition

Trying to establish a standard easy blog collection site for categorizing blogs

如何分类博客

---

- [blog-composition](#blog-composition)
  - [不愿运行一个 API 程序，如何获取博客的分类](#不愿运行一个-api-程序如何获取博客的分类)
  - [愿意运行一个 API 程序，如何获取博客的分类](#愿意运行一个-api-程序如何获取博客的分类)
    - [如何统计文章数量](#如何统计文章数量)
    - [API 设计](#api-设计)
    - [如何根据 API 获取到的值分类博客](#如何根据-api-获取到的值分类博客)
  - [博客园如何设计分类系统](#博客园如何设计分类系统)

---

## 不愿运行一个 API 程序，如何获取博客的分类

1. 让站长自己标记\声明\选择是生活博客还是技术博客
2. 在站点主页元数据内标记自己站点有多少技术类文章，多少非技术类文章

## 愿意运行一个 API 程序，如何获取博客的分类

站长运行一个 API 程序，用于展示自己的博客文章数量。

### 如何统计文章数量

1. 站长自统计
2. 程序自统计
   - 开发一个程序，用于收集站长给自己文章的分类。
   - 程序统计方法可以是从后台接口获取数据，也可以是通过前端样式获取。

### API 设计

API 可固定在某一链接， url\blog-composition， api 设计符合如 RESTful API 之类的标准。

API 获取样例

```json
{
    "technical": 15,
    "other": 4
}
```

### 如何根据 API 获取到的值分类博客

博客园爬虫在读取到 API 返回值后，根据站点文章类型占比就可以把博客分类为

- 技术文章占比 = 100% ：纯正的技术博客
- 100%> 技术文章占比 >=70% ：偶尔发点技术以外的东西
- 70%> 技术文章占比 >=50% ：差不多但是技术文章更多一点
- 50%> 技术文章占比 >=30% ：差不多但是非技术文章更多点
- 30%> 技术文章占比 >0% ：偶尔发点技术文章
- 技术文章占比 = 0% ：纯正的非技术博客

## 博客园如何设计分类系统

- 如果这个站长运行了这个 API 程序，就按照技术文章占比来分类。
- 如果这个站长没有运行这个 API 程序，就按照站长自己标记\声明\选择的分类为生活博客或技术博客
