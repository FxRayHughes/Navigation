# Navigation (no-entity)
Minecraft 无实体寻路（部分代码来自 Minecraft 核心）  

## 前言
_在 Adyeshach 开发的时候就想写这个东西了，不过那个时候写了一点没坚持下来，这一次轮到 Chemdah 又需要了，但是实在是不想用 Adyeshach 的那个脑残办法。  
硬着头皮对着 mcp 耗了 48 小时才读了不到 1000 行，直到现在 BinaryHeap 还是反编译过来的。  
刚开始写想着偷个懒直接复制，没想到测试的时候不是寻不出来就是卡爆，还不知道哪里的问题。草了。  
所以又耗一天把 WalkNodeEvaluator 照着写了一份带注释的版本，不过现在也仅仅支持标准陆地生物的寻路方式。__

## 使用方法
```kotlin
// 起点
val start: Location = ...
// 终点
val end: Location = ...
// 创建单位代替 Minecraft 实体，并具有高度宽度等。
val entity = NodeEntity(start, height = 2.0, width = 1.0)
// 创建 Pathfinder
val pathfinder = Navigation.create(entity)
// 开始寻路并返回路径结果
val path = pathfinder.findPath(end, distance = 16)
// 打印路径
if (path != null) {
    path.nodes.forEach { node ->
        println(node)
    }
}
```
