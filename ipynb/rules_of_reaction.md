# yadwicksSolution
破电子裁判的运行规则
<script 
  src="https://cdn.bootcss.com/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML"></script>
## 烧杯(Beaker)
- 属性:
  - 物质
    - 物质
      - ID : 数量
        (初始为 $H_2O$ :56)
  - pH
    - 初始为7
  - pH保持回合:
    ```
    烧杯pH大于7+A或小于7-A的回合数量
    当pH为7-A到7+A时重制为0
    ```
  - 玩家编号
- 操作:
  - 加入物质
  - 烧杯反应
## 物质种类:
  - $H_2O$(H2O)
    - 溶剂, 默认为56
  - 离子(Ion)
    - 溶液的溶质部分, 不包括$H^+$,$OH^-$
    - 离子的属性:
      - 氧化还原性: int (0为不会发生氧化还原反应)
      - 电荷: int (不为0)
- Z物质(Subs)
  - 稳定的物质
  - Z物质的属性:
    - 氧化还原性: int (0为不会发生氧化还原反应)
- Zs类物质(SubsZs)
  - 沉淀, 如$CaCO_3$
- Zg类物质(SubsZg)
  - 气体, 如$H_2, NH_3, SO_2$
## 烧杯反应(或者这里叫变化)
### X类反应(reactionX)
$X$和$H_2O$的反应
$$X + H_2O = Y + Zg↑/Zs↓$$
- X类反应的优先度最高
- X类:
    - [反应物(ID, 数量)], [生成物(ID, 数量)]

`按照真实世界的说法, X类反应实际上是OR类反应的一种……`
### I类反应(reactionI)
    某物质的电离
$$CiAi = Ci^{n+} + Ai^{n-}$$
  - 反应优先度低于OR类

- I类:
    - [反应物(ID, 数量)], 条件, [生成物(ID, 数量)]

`按照真实世界的说法, I类反应实际上不是化学反应……`

### IOR类反应(reactionIOR)
     某物质电离出的离子与溶液中原有的离子发生氧化还原反应
   $$M^{m} + N^{n} = M^{p} + N^{q}$$
- 反应优先度低于I类
- IOR类:
    - [反应物(ID, 数量)], 条件, [生成物(ID, 数量)]
### IE类反应(reactionIE) 
     复分解反应/离子交换
 $$Ci^{n+} + Ai^{n-} = Zg↑/Zs↓$$
- IE类反应的优先度在IOR之后
- IE类:
    - [反应物(ID, 数量)], 条件, [生成物(ID, 数量)]
### DH类反应(reactionDH)
    双水解反应
  - 优先度低于IE类
   - DH类:
      - [反应物(ID, 数量)], [生成物(ID, 数量)]
### F类反应(reactionF)
  - 实际是个自动过程
  - 清除烧杯中所有Zs类物质
  - 清除烧杯中所有Zg类物质
  - F类:
    - [反应物(ID, 数量)]
### 走一遍这个流程看看?
