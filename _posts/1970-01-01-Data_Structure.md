---
layout: default
title: 数据结构
category: MOOC
---

推荐教辅和资料：

1．《数据结构》，陈越、何钦铭、徐镜春、魏宝刚、杨枨 编著，高等教育出版社，2012年4月
2．《数据结构学习与实验指导》，陈越、何钦铭、徐镜春、魏宝刚、杨枨 编著，高等教育出版社，2013年5月
3． 课程练习网站：
PTA（Programming Teaching Assistant）：http://pta.patest.cn/ 本课程的编程练习将在这里布置。
PAT（Programming Ability Test）官网：http://www.patest.cn/ 提供全部考试真题。 


课后练习平台：PTA（https://pta.patest.cn 上有《中国大学MOOC-陈越、何钦铭-数据结构-2016秋》习题集）
以后都从PTA的首页点“进入题库”，在《中国大学MOOC-陈越、何钦铭-数据结构-2017春》这个题目集中完成作业。

---

[TOC]

## 

当讨论如何组织数据时，首先必须明确数据规模。不同的规模适合不同的组织方式。

解决问题方法的效率，跟数据的组织方式有关。[e.g. 图书摆放]
解决问题方法的效率，跟空间的利用效率有关。[e.g. PrintN 函数实现]

**例2：写程序实现一个函数PrintN，使得传入一个正整数为N的参数后，能顺序打印从1到N的全部正整数**
```
/*循环实现*/
void PrintN(int N)
{
	int i;
	for (i = 1; i <= N; i++) {
		printf("%d\n", i);
	}
	return;
}
```

```
/*递归实现*/
void PrintN(int N)
{
	if (N) {
		PrintN(N-1);
		printf("%d\n", N);
	}
	return;
}
```







