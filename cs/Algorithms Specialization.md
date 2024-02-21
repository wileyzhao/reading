# part 1
recommend a course about math: “Mathematics for computer science”(Eric Lehman/Tom Layden)

### quick sort
O(nlogn), especially choose the median or random pivot

### random contraction algorithms
<img width="753" alt="0F2E3B06-1890-4B11-BC0B-858F39138C03" src="https://github.com/wileyzhao/reading/assets/21215474/cc6940a6-d120-46ab-be2d-47db111c9bbc">

这样一次运算的复杂度为O(m)，我们可以看到，这样随机的过程返回的结果是不确定的，找到的割并不一定是最小的，事实上可以证明，一次运行找到最小割的概率最低为1/(n2)，那么，将上述算法重复执行(n2)lnn次，我们可以以低于的1/n的失败概率获得最小割，这就是Karger全局最小割算法的基本思想，时间复杂度为O(n2mlnn)。


# Graph Search, Shortest Paths, and Data Structures

