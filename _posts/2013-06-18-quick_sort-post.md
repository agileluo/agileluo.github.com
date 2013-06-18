---
layout: post
title: "快速排序"
description: ""
category: 
tags: [算法]
---


###1，基础快速排序算法  

详细代码参见[QuickSort.java](https://github.com/agileluo/algorithms_learn/blob/master/sort/QuickSort.java)
<pre>
public static void sort(Comparable[] a) {
		sort(a, 0, a.length-1);
}
private static void sort(Comparable[] a, int lo, int hi) {
	if( hi <= lo ) return;
	int j = partition(a, lo, hi);
	sort(a, lo, j-1);
	sort(a, j + 1, hi);
}
private static int partition(Comparable[] a, int lo, int hi) {
	int i = lo, j = hi + 1;
	Comparable v = a[lo];
	while(true){
		while(SortExample.less(a[++i], v)) if( i == hi) break;
		while(SortExample.less(v, a[--j])) if( j == lo) break;
		if( i >= j) break;
		SortExample.exch(a, i, j);
	}
	SortExample.exch(a, lo, j);
	return j;
}
</pre>

###2，三向切分快速排序算法(熵最优)  

详细代码参见[Quick3Sort.java](https://github.com/agileluo/algorithms_learn/blob/master/sort/Quick3Sort.java)
<pre>
public static void sort(Comparable[] a) {
		sort(a, 0, a.length-1);
}
private static void sort(Comparable[] a, int lo, int hi) {
	if(hi <= lo) return;
	int lt = lo, i = lo + 1, gt = hi;
	Comparable v = a[lo];
	while(i <= gt){
		int comp = a[i].compareTo(v);
		if ( comp < 0) SortExample.exch(a, lt++, i++);
		else if( comp > 0) SortExample.exch(a, i, gt--);
		else i++;
	}
	sort(a, lo, lt-1);
	sort(a, gt + 1, hi);
}
</pre>