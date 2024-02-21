# Week 1
## Bellman-Ford Algorithm
Bellman-Ford 算法是一种用于计算带权有向图中单源最短路径（SSSP：Single-Source Shortest Path）的算法。该算法由 Richard Bellman 和 Lester Ford 分别发表于 1958 年和 1956 年，而实际上 Edward F. Moore 也在 1957 年发布了相同的算法，因此，此算法也常被称为 Bellman-Ford-Moore 算法。
Bellman-Ford 算法和 Dijkstra 算法同为解决单源最短路径的算法。对于带权有向图 G = (V, E)，Dijkstra 算法要求图 G 中边的权值均为非负，而 Bellman-Ford 算法能适应一般的情况（即存在负权边的情况）。一个实现的很好的 Dijkstra 算法比 Bellman-Ford 算法的运行时间要低。
Bellman-Ford 算法采用[动态规划（Dynamic Programming）](http://www.cnblogs.com/gaochundong/p/algorithmic_paradigms.html)进行设计，实现的时间复杂度为 O(V*E)，其中 V 为顶点数量，E 为边的数量。Dijkstra 算法采用[贪心算法（Greedy Algorithm）](http://www.cnblogs.com/gaochundong/p/algorithmic_paradigms.html)范式进行设计，普通实现的时间复杂度为 O(V2)，若基于 [Fibonacci heap](http://www.cnblogs.com/gaochundong/p/fibonacci_heap.html) 的最小优先队列实现版本则时间复杂度为 O(E + VlogV)。
Bellman-Ford 算法描述：
1、创建源顶点 v 到图中所有顶点的距离的集合 distSet，为图中的所有顶点指定一个距离值，初始均为 Infinite，源顶点距离为 0；
2、计算最短路径，执行 V - 1 次遍历；
    对于图中的每条边：如果起点 u 的距离 d 加上边的权值 w 小于终点 v 的距离 d，则更新终点 v 的距离值 d；
3、检测图中是否有负权边形成了环，遍历图中的所有边，计算 u 至 v 的距离，如果对于 v 存在更小的距离，则说明存在环；
## Greedy Algorithms
**“Definition”:Iteratively make “myopic” decisions, hope everything works out at the end.**
**它总是做出局部最优的选择，寄希望(证明)这样的选择能够导致全局最优解。**
Contrast with Divide & Conquer
1/    easy to propose multiple greedy algorithms for many problems 
2/    easy running time analysis
3/    hard to establish correctness
DANGER: Most greedy algorithms are NOT correct. 
贪心算法在有最优子结构的问题中尤为有效。最优子结构的意思是局部最优解能决定全局最优解。简单地说，问题能够分解成子问题来解决，子问题的最优解能递推到最终问题的最优解。
贪心算法与动态规划的不同在于它对每个子问题的解决方案都做出选择，不能回退。动态规划则会保存以前的运算结果，并根据以前的结果对当前进行选择，有回退功能。
贪心法可以解决一些最优化问题，如：求图中的最小生成树、求哈夫曼编码……对于其他问题，贪心法一般不能得到我们所要求的答案。一旦一个问题可以通过贪心法来解决，那么贪心法一般是解决这个问题的最好办法。由于贪心法的高效性以及其所求得的答案比较接近最优结果，贪心法也可以用作辅助算法或者直接解决一些要求结果不特别精确的问题。
步骤：

1. 建立数学模型来描述问题。
2. 把求解的问题分成若干个**子问题**。
3. 对每一子问题求解，得到子问题的局部最优解。
4. 把子问题的解局部最优解合成原来解问题的一个解。

实现该算法的过程：
从问题的某一初始解出发；while 能朝给定总目标前进一步 do ,求出可行解的一个解元素；
最后，由所有解元素组合成问题的一个可行解。
**Application：Optimal Caching**
**A Scheduling Application**
**Minimum Spanning Tree(MST)**
最小生成树是一副连通加权无向图中一棵权值最小的生成树。
在一给定的无向图 G = (V, E) 中，(u, v) 代表连接顶点 u 与顶点 v 的边（即 {\displaystyle (u,v)\in E}![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489993976-fd6c29c4-4966-4ee8-9aa2-afee98e3a82f.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=u731e0a5d&originHeight=20&originWidth=71&originalType=url&ratio=2&rotation=0&showTitle=false&size=4169&status=done&style=none&taskId=u2eaa6f6b-af23-4a1b-ad15-4ff0ae09bb1&title=)），而 w(u, v) 代表此边的权重，若存在 T 为 E 的子集（即 {\displaystyle T\subseteq E}![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489993988-f6dca10c-c871-4b6e-8588-4ef2884e369c.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=u16a0c68e&originHeight=17&originWidth=47&originalType=url&ratio=2&rotation=0&showTitle=false&size=2600&status=done&style=none&taskId=uc1a29827-6e9b-47ec-8c40-c71d8bfde89&title=)）且 (V, T) 为树，使得
{\displaystyle w(T)=\sum _{(u,v)\in T}w(u,v)}![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489994007-1f19894c-6252-4027-aa4f-214145ebe8d0.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=ubd29d496&originHeight=43&originWidth=153&originalType=url&ratio=2&rotation=0&showTitle=false&size=6492&status=done&style=none&taskId=u29086362-79ff-4288-8771-71066718371&title=)

的 w(T) 最小，则此 T 为 G 的最小生成树。
最小生成树其实是最小权重生成树的简称。最小生成树是一副连通加权无向图中一棵权值最小的生成树。
在一给定的无向图 G = (V, E) 中，(u, v) 代表连接顶点 u 与顶点 v 的边（即 {\displaystyle (u,v)\in E}![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489994034-7beb1430-780e-41b5-bd3b-56a5bc549dc8.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=u590fe70f&originHeight=20&originWidth=71&originalType=url&ratio=2&rotation=0&showTitle=false&size=4169&status=done&style=none&taskId=uec7afb5d-f7ae-409f-bc2f-0bc692cf9f2&title=)），而 w(u, v) 代表此边的权重，若存在 T 为 E 的子集（即 {\displaystyle T\subseteq E}![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489994039-b9683512-5c75-4ee1-9df9-b34b14b3f716.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=u84cb0d27&originHeight=17&originWidth=47&originalType=url&ratio=2&rotation=0&showTitle=false&size=2600&status=done&style=none&taskId=u3acb8263-39d0-4e8f-8f0b-63541ed5421&title=)）且 (V, T) 为树，使得
{\displaystyle w(T)=\sum _{(u,v)\in T}w(u,v)}![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489994732-60c814a4-09ca-4d87-9222-6f330d20c04e.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=ud99790a8&originHeight=43&originWidth=153&originalType=url&ratio=2&rotation=0&showTitle=false&size=6492&status=done&style=none&taskId=u078cbd51-b473-45c7-b531-8d827979e7d&title=)

的 w(T) 最小，则此 T 为 G 的最小生成树。
最小生成树其实是最小权重生成树的简称。
最小生成树是连通无向带权图的一个子图，要求能够连接图中的所有顶点、无环、且路径的权重和为所有路径中最小的.
**kruskal算法的基本思想：**
1.首先将G的n个顶点看成n个孤立的连通分支（n个孤立点）并将所有的边按权从小大排序。
2.按照边权值递增顺序，如果加入边后存在圈则这条边不加，直到形成连通图
对2的解释：如果加入边的两个端点位于不同的连通支，那么这条边可以顺利加入而不会形成圈
![image.png](https://cdn.nlark.com/yuque/0/2024/png/152585/1708489996310-c9f103bb-8063-4945-a2b1-e7f4f939d655.png#averageHue=%23f8f4eb&clientId=uc2ba2b50-8f55-4&from=paste&id=u58f7a025&originHeight=968&originWidth=1560&originalType=url&ratio=2&rotation=0&showTitle=false&size=235137&status=done&style=none&taskId=uebffa9bf-c0a6-45b4-97c6-6fae3a565c9&title=)![image.png](https://cdn.nlark.com/yuque/0/2024/png/152585/1708489999823-0e1f9d7e-224b-4f53-ac23-f5884c7b3ff0.png#averageHue=%23f9f8f7&clientId=uc2ba2b50-8f55-4&from=paste&id=ue5086725&originHeight=1028&originWidth=1686&originalType=url&ratio=2&rotation=0&showTitle=false&size=612972&status=done&style=none&taskId=uf58821b4-b873-4d14-8a86-27aa905c8aa&title=)
**Prim’s MST Algorithm**
此算法可以称为“加点法”，每次迭代选择代价最小的边对应的点，加入到最小生成树中。算法从某一个顶点s开始，逐渐长大覆盖整个连通网的所有顶点。
图的所有顶点集合为VV；初始令集合u={s},v=V−uu={s},v=V−u;
在两个集合u,vu,v能够组成的边中，选择一条代价最小的边(u0,v0)(u0,v0)，加入到最小生成树中，并把v0v0并入到集合u中。
重复上述步骤，直到最小生成树有n-1条边或者n个顶点为止。
![image.png](https://cdn.nlark.com/yuque/0/2024/png/152585/1708490001427-30fed690-8e6a-40ca-b99c-f858202beb4f.png#averageHue=%23f9f8f7&clientId=uc2ba2b50-8f55-4&from=paste&id=uf2032413&originHeight=1030&originWidth=1602&originalType=url&ratio=2&rotation=0&showTitle=false&size=778697&status=done&style=none&taskId=u6fea4493-43ed-4008-a523-8c1e97e8583&title=)
# week2:kruskal MST Algorithms && Union-Find
### 并查集(Union-Find)算法
在计算机科学中，并查集是一种树型的数据结构，用于处理一些不交集（Disjoint Sets）的合并及查询问题。有一个联合-查找算法（union-find algorithm）定义了两个用于此数据结构的操作：
![image.png](https://cdn.nlark.com/yuque/0/2024/png/152585/1708489995092-aa28487f-4d6d-4131-b913-fb61357d5d56.png#averageHue=%23000000&clientId=uc2ba2b50-8f55-4&from=paste&id=u074e62d7&originHeight=33&originWidth=360&originalType=url&ratio=2&rotation=0&showTitle=false&size=4390&status=done&style=none&taskId=u509e784a-5e9d-421d-92f4-16fcb8e10fd&title=)

MakeSet建立了8个元素。
![image.png](https://cdn.nlark.com/yuque/0/2024/png/152585/1708489995453-0b9cb6a2-540d-441a-a31a-a9c84d2bbfd6.png#averageHue=%23000000&clientId=uc2ba2b50-8f55-4&from=paste&id=u8f0959d4&originHeight=33&originWidth=360&originalType=url&ratio=2&rotation=0&showTitle=false&size=2750&status=done&style=none&taskId=u408adb00-eb3d-4e7c-89fb-541f4736ee3&title=)

                在几次Union操作后，一些集合合并在一起。

- **Find：确定元素属于哪一个子集。它可以被用来确定两个元素是否属于同一子集。**
- **Union：将两个子集合并成同一个集合。**

由于支持这两种操作，一个不相交集也常被称为联合-查找数据结构（union-find data structure）或合并-查找集合（merge-find set）。其他的重要方法，MakeSet，用于建立单元素集合。有了这些方法，许多经典的[划分问题](https://zh.wikipedia.org/w/index.php?title=%E5%88%92%E5%88%86%E9%97%AE%E9%A2%98&action=edit&redlink=1)可以被解决。
为了更加精确的定义这些方法，需要定义如何表示集合。一种常用的策略是为每个集合选定一个固定的元素，称为代表，以表示整个集合。接着，Find(x) 返回 x 所属集合的代表，而 Union 使用两个集合的代表作为参数。
第一个优化“按秩合并”，即总是将更小的树连接至更大的树上。因为影响运行时间的是树的深度，更小的树添加到更深的树的根上将不会增加秩除非它们的秩相同。在这个算法中，术语“秩”替代了“深度”，因为同时应用了路径压缩时（见下文）秩将不会与高度相同。单元素的树的秩定义为0，当两棵秩同为r的树联合时，它们的秩r+1。只使用这个方法将使最坏的运行时间提高至每个MakeSet、Union或Find操作![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489995886-1232afbf-4ebb-49ee-b0c9-6a664d1e1a7d.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=u928ed9cf&originHeight=20&originWidth=60&originalType=url&ratio=2&rotation=0&showTitle=false&size=4057&status=done&style=none&taskId=u4b6e28f8-2448-4457-b1cd-4e63b3944e9&title=)。优化后的MakeSet和Union伪代码：
**function**_**MakeSet**_**(x)**
     x.parent := x
     x.rank   := 0
**function**_**Union**_**(x, y)**
     xRoot :=_Find_(x)
     yRoot :=_Find_(y)
     if xRoot == yRoot
         return
    // x和y不在同一个集合，合并它们。
     if xRoot.rank < yRoot.rank
         xRoot.parent := yRoot
     else if xRoot.rank > yRoot.rank
         yRoot.parent := xRoot
     else
         yRoot.parent := xRoot
         xRoot.rank := xRoot.rank + 1
第二个优化，称为“路径压缩”，是一种在执行“查找”时扁平化树结构的方法。关键在于在路径上的每个节点都可以直接连接到根上；他们都有同样的表示方法。为了达到这样的效果，Find递归地经过树，改变每一个节点的引用到根节点。得到的树将更加扁平，为以后直接或者间接引用节点的操作加速。这儿是Find：
**function**_Find_(x)
     if x.parent != x
        x.parent :=_Find_(x.parent)
     return x.parent
这两种方法的优势互补，同时使用二者的程序每个操作的[平均](https://zh.wikipedia.org/wiki/%E5%B9%B3%E6%91%8A%E5%88%86%E6%9E%90)时间仅为![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489996204-d425c991-6e19-4ab4-9c64-3fd825e7c2b6.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=u2c586cd1&originHeight=20&originWidth=59&originalType=url&ratio=2&rotation=0&showTitle=false&size=2984&status=done&style=none&taskId=u5111ca70-6f80-4fe5-a44a-f7237faf45f&title=)，![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489996643-6ccf6ba6-1201-4b82-8cdd-33d479f281e9.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=ueb83f514&originHeight=20&originWidth=34&originalType=url&ratio=2&rotation=0&showTitle=false&size=2471&status=done&style=none&taskId=u4bf85b5f-4e62-415f-91b0-ac6cbc45f49&title=)是![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489996795-348dc2d8-e673-441a-8306-bba92140b872.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=u97372c02&originHeight=20&originWidth=138&originalType=url&ratio=2&rotation=0&showTitle=false&size=4871&status=done&style=none&taskId=u0cc57855-3688-46ab-ba0f-95094a6a292&title=)的[反函数](https://zh.wikipedia.org/wiki/%E5%8F%8D%E5%87%BD%E6%95%B8)，其中![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489996980-81b9bcfd-1297-4448-a2b2-f908d05a7a80.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=u07fccda0&originHeight=16&originWidth=13&originalType=url&ratio=2&rotation=0&showTitle=false&size=1087&status=done&style=none&taskId=u2429bfca-4340-4c1a-8080-7c9ac67f8fc&title=)是急速增加的[阿克曼函数](https://zh.wikipedia.org/wiki/%E9%98%BF%E5%85%8B%E6%9B%BC%E5%87%BD%E6%95%B0)。因为![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489997603-840f4a44-f956-4ad9-a598-4249701fd694.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=u6a9b04e8&originHeight=20&originWidth=34&originalType=url&ratio=2&rotation=0&showTitle=false&size=2471&status=done&style=none&taskId=u12c37ebd-5d9f-4b93-a73b-6aeec23a217&title=)是其的反函数，故![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489997656-57868c26-980f-4bdd-a1e9-316dd023b054.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=u5bd16d1d&originHeight=20&originWidth=34&originalType=url&ratio=2&rotation=0&showTitle=false&size=2471&status=done&style=none&taskId=ue2858eae-95e5-44ba-87a9-f900c5cb40a&title=)在![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489997655-94bbfecd-c55c-47ee-8e31-1829433f084e.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=u3bf54dd4&originHeight=12&originWidth=10&originalType=url&ratio=2&rotation=0&showTitle=false&size=1129&status=done&style=none&taskId=u1675ac9e-eaac-4b55-b562-55bb6c90e6f&title=)十分巨大时还是小于5。因此，平均运行时间是一个极小的常数。
实际上，这是渐近最优算法：Fredman和Saks在1989年解释了![image.png](https://cdn.nlark.com/yuque/0/2024/svg/152585/1708489998279-02c23db7-4a01-406d-af1d-e072e7f9ee14.svg#clientId=uc2ba2b50-8f55-4&from=paste&id=u5967147c&originHeight=20&originWidth=59&originalType=url&ratio=2&rotation=0&showTitle=false&size=3209&status=done&style=none&taskId=u8fee07fa-bf1f-4c66-9215-389aed67912&title=)的平均时间内可以获得任何并查集。
### simhash
假设我们有海量的文本数据，我们需要根据文本内容将它们进行去重。对于文本去重而言，目前有很多NLP相关的算法可以在很高精度上来解决，但是我们现在处理的是大数据维度上的文本去重，这就对算法的效率有着很高的要求。而局部敏感hash算法可以将原始的文本内容映射为数字（hash签名），而且较为相近的文本内容对应的hash签名也比较相近。SimHash算法是Google公司进行海量网页去重的高效算法，它通过将原始的文本映射为64位的二进制数字串，然后通过比较二进制数字串的差异进而来表示原始文本内容的差异。
![image.png](https://cdn.nlark.com/yuque/0/2024/png/152585/1708490000708-96db550c-97fc-4127-b455-5054035ab5de.png#averageHue=%23c5c5c3&clientId=uc2ba2b50-8f55-4&from=paste&id=u516d0d7e&originHeight=1134&originWidth=1470&originalType=url&ratio=2&rotation=0&showTitle=false&size=285019&status=done&style=none&taskId=ua1b1a687-e57d-45e1-85a2-fcafc3be305&title=)
**存储**： 
1、将一个64位的simhash签名拆分成4个16位的二进制码。（图上红色的16位） 
2、分别拿着4个16位二进制码查找当前对应位置上是否有元素。（放大后的16位） 
3、对应位置没有元素，直接追加到链表上；对应位置有则直接追加到链表尾端。（图上的 S1 — SN） 
**查找**： 
1、将需要比较的simhash签名拆分成4个16位的二进制码。 
2、分别拿着4个16位二进制码每一个去查找simhash集合对应位置上是否有元素。 
3、如果有元素，则把链表拿出来顺序查找比较，直到simhash小于一定大小的值，整个过程完成。 
**原理**： 
借鉴hashmap算法找出可以hash的key值，因为我们使用的simhash是局部敏感哈希，这个算法的特点是只要相似的字符串只有个别的位数是有差别变化。那这样我们可以推断两个相似的文本，至少有16位的simhash是一样的。具体选择16位、8位、4位，大家根据自己的数据测试选择，虽然比较的位数越小越精准，但是空间会变大。分为4个16位段的存储空间是单独simhash存储空间的4倍。之前算出5000w数据是 382 Mb，扩大4倍1.5G左右，还可以接受 
### Hamming distance（汉明距离）
# week3:Huffman codes; introduction to dynamic programming
## Huffman Coding
在计算机数据处理中，霍夫曼编码使用变长编码表对源符号（如文件中的一个字母）进行编码，其中变长编码表是通过一种评估来源符号出现机率的方法得到的，出现机率高的字母使用较短的编码，反之出现机率低的则使用较长的编码，这便使编码之后的字符串的平均长度、期望值降低，从而达到无损压缩数据的目的。
Huffman编码就是利用每个字符出现频率的不一致，用长短不一的0、1字节来表示不同的字符以减少总数据大小。 假设我们有一包含10000个字符的文件，这些字 符仅由6个不同的字符组成，就设这6个字符分别为“abcdef”，下面的表给出了 这6个字符在整个文件中的占比，和两种不同的编码方式。
![image.png](https://cdn.nlark.com/yuque/0/2024/png/152585/1708489998478-66d0f1bb-31ea-4af0-96d6-7012e706a1b2.png#averageHue=%23d7bc96&clientId=uc2ba2b50-8f55-4&from=paste&id=u83945e72&originHeight=169&originWidth=860&originalType=url&ratio=2&rotation=0&showTitle=false&size=19882&status=done&style=none&taskId=ubd1f8807-fd0f-4add-90ed-5cf78b6d5b4&title=)

上例中固定长度的编码方式最少需要三位。那么整个文件的长度大小为300,000 bits，而对于可变长度的编码方式其使用大小为：
(45 * 1 + 13 * 3 + 12 * 3 + 16 * 3 + 9 * 4 + 5 * 4) · 1,000 = 224,000 bits
使用第二种编码方式能比第一种方式节约大约25%的空间。上述变长编码的方式实 际上是一种名为前缀编码的编码方式。
赫夫曼编码是指赫夫曼提供的一种构建最优前缀编码的方法。其方法是总选取权 重最小的两个结点_x_和_y_合并成一个结点_z_,并用_z_代替它们，再从中选出两 个权重最小的结点。如是反复。图解： 
![image.png](https://cdn.nlark.com/yuque/0/2024/png/152585/1708490000079-fa89e30e-e56c-49e3-83a2-301df0558c7b.png#averageHue=%23faf9f9&clientId=uc2ba2b50-8f55-4&from=paste&id=ub02e38a7&originHeight=497&originWidth=624&originalType=url&ratio=2&rotation=0&showTitle=false&size=98718&status=done&style=none&taskId=u302607bf-c95f-40a1-80a9-e512a7557d7&title=)
 根据节点的个数以及权值的不同，赫夫曼树的形状也各不相同，赫夫曼树具有如下特性：
对于同一组权值，所能得到的赫夫曼树不一定是唯一的。
赫夫曼树的左右子树可以互换，因为这并不影响树的带权路径长度。
带权值的节点都是叶子节点，不带权值的节点都是某棵子二叉树的根节点。
权值越大的节点越靠近赫夫曼树的根节点，权值越小的节点越远离赫夫曼树的根节点。
赫夫曼树中只有叶子节点和度为2的节点，没有度为1的节点。
一棵有n个叶子节点的赫夫曼树共有2n-1个节点。
**huffman编码思路**
霍夫曼树本质是一种贪心的思想，他是按照编码过程中每个字符出现的频率进行无前缀的编码。即：对给出的n个字符和其出现频率，每次在小根堆取出出现频率最低的字符（当然还要删除该两节点）作为一个新节点的左右子树，然后该新节点再放入小根堆。不断重复上述操作，知道小根堆只有一个节点，此时就建成一棵二叉树了。不难看出只有每个叶子中才有字符，而该叶子中的字符对应的编码就是从根到他的路径。
**huffman解码思路**
解码的思想有很多比如可以把字符和编码记忆化，然后扫描字符串不断匹配。假设字符串长为n那么复杂度在O(n^2) 
还有一种更好的思路就是将按照0和1进行路径上的移动。 
如果是0就进入左子树如果是1就进入右子树。 
如果到达叶子节点，（叶子节点的一个特性就是左右子树均为空）就从重新回根节点。
## Dynamic Programming
动态规划常常适用于有重叠子问题和最优子结构性质的问题，动态规划方法所耗时间往往远少于朴素解法。
动态规划背后的基本思想非常简单。大致上，若要解一个给定问题，我们需要解其不同部分（即子问题），再根据子问题的解以得出原问题的解。
通常许多子问题非常相似，为此动态规划法试图仅仅解决每个子问题一次，从而减少计算量：一旦某个给定子问题的解已经算出，则将其记忆化存储，以便下次需要同一个子问题解之时直接查表。这种做法在重复子问题的数目关于输入的规模呈指数增长时特别有用
**Divide-Conquer && Dynamic Programming**
**分治法是指将问题划分成一些独立地子问题，递归地求解各子问题，然后合并子问题的解而得到原问题的解。与此不同，动态规划适用于子问题独立且重叠的情况，也就是各子问题包含公共的子子问题。**在这种情况下，若用分治法则会做许多不必要的工作，即重复地求解公共的子问题。动态规划算法对每个子子问题只求解一次，将其结果保存在一张表中，从而避免每次遇到各个子问题时重新计算答案。
**path graph：链图**
**Max independent set**
最大独立集： 顶点集V中取 K个顶点，其两两间无连接，则k的最大集合，就为最大独立集。
该课程用了链图的最大独立集做例子，不是很好理解，但一旦想通，过程还是很简单的。
拿课后的作业来看，求链图的最大独立集，需要先用动态规划的算法，将所有顶点的最大数（即max{A[i-1],A[i-2]+wi}）都记录在map中。再通过最大独立集的概念去获得最大独立集。
A Reconstruction Algorithm
Let A = filled-in array:
0123...n
- Let S = ∅
- While i ≥ 1 [scan through array from right to left]
-IfA[i−1]≥A[i−2]+wi [i.e. case1wins]- Decrease i by 1
- Else [i.e., case 2 wins]
-Addvi toS,decreasei by2
- Return S
Claim: [By induction + our case analysis] Final output S is a
max-weight IS of G.Running time: O(n)
# week4：the knapsack problem, sequence alignment, and optimal binary search trees
**伪多项式时间**
在计算理论领域中，若一个数值算法的时间复杂度可以表示为输入数值规模N的多项式，但其运行时间与输入数值规模N的二进制位数呈指数增长关系，则称其时间复杂度为伪多项式时间。这是由于，N的值是N的位数的幂，故该算法的时间复杂度实际上应视为输入数值N的位数的幂。
一个具有伪多项式时间复杂度的NP完全问题称之为弱NP完全问题，而在P!=NP的情况下，若一个NP完全问题被证明没有伪多项式时间复杂度的解，则称之为强NP完全问题。
**0-1背包问题问题分析：**
用动态规划解问题首先要有效的找出子问题，可以通过这个子问题得推得原问题的解，通常子问题的实质是和原问题相同的，只是规模上的缩小，
也就是说子问题和原问题可以有相同的表示形式，问题可通过不断的缩小规模（一般都会有一个界限）能找到子问题的解。
这个问题要求解的是能用背包带走的物品的最大价值。
mp[x][y] 表示体积不超过 y 且可选前 x 种物品的情况下的最大总价值
那么原问题可表示为 mp[n][V]
递归关系：

1. mp[0][y] = 0
2. mp[x][0] = 0
3. 当 v[x] > y 时，mp[x][y] = mp[x-1][y]
4. 当 v[x] <= y 时，mp[x][y] = max{ mp[x-1][y], p[x] + mp[x-1][y-v[x]] }

解释如下：

1. 表示体积不超过 y 且可选前 0 种物品的情况下的最大总价值，没有物品可选，所以总价值为 0
2. 表示体积不超过 0 且可选前 x 种物品的情况下的最大总价值，没有物品可选，所以总价值为 0
3. 因为 x 这件物品的体积已经超过所能允许的最大体积了，所以肯定不能放这件物品， 那么只能在前 x-1 件物品里选了
4. x 这件物品可能放入背包也可能不放入背包，所以取前两者的最大值就好了， 这样就将前两种情况都包括进来了

通过计算_A_(_n_, _W_)即得到最终结果。为提高算法性能，我们把先前计算的结果存入表中。因此算法需要的时间和空间都为O(_nW_)，通过对算法的改进，空间的消耗可以降至O(_W_)。
### Sequence Alignment
![image.png](https://cdn.nlark.com/yuque/0/2024/png/152585/1708489999699-8d489b5d-fbef-47b0-93af-fed538586767.png#averageHue=%23f7f5f4&clientId=uc2ba2b50-8f55-4&from=paste&id=udab2f0c4&originHeight=288&originWidth=487&originalType=url&ratio=2&rotation=0&showTitle=false&size=52133&status=done&style=none&taskId=u6c0f5785-97e0-4f58-95af-dac617c4fc4&title=)**

### optimal binary search trees
**最优二叉查找树：**
给定n个互异的关键字组成的序列K=<k1,k2,...,kn>，且关键字有序（k1<k2<...<kn），我们想从这些关键字中构造一棵二叉查找树。对每个关键字ki，一次搜索搜索到的概率为pi。可能有一些搜索的值不在K内，因此还有n+1个“虚拟键”d0,d1,...,dn，他们代表不在K内的值。具体：d0代表所有小于k1的值，dn代表所有大于kn的值。而对于i = 1,2,...,n-1,虚拟键di代表所有位于ki和ki+1之间的值。对于每个虚拟键，一次搜索对应于di的概率为qi。要使得查找一个节点的期望代价（代价可以定义为：比如从根节点到目标节点的路径上节点数目）最小，就需要建立一棵最优二叉查找树。
