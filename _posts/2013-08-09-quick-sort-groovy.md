---
layout: post
title: "groovy快速排序"
description: ""
category: 
tags: [算法]
---

###1，groovy快速排序算法 
详细代码参见[listInAction.groovy](https://github.com/agileluo/groovy_learn/blob/master/src/datetype/collective/listInAction.groovy)
<pre>
def quickSort(list){
	if (list.size() < 2) return list
	def pivot = list[list.size().intdiv(2)]
	def left = list.findAll { it < pivot }
	def middle = list.findAll { it == pivot }
	def right = list.findAll { it > pivot }
	return (quickSort(left) + middle + quickSort(right))
}
</pre>
代码太简洁了，有么有