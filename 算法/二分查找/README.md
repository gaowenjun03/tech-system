# 二分查找

1、定义

二分查找又称折半查找，它是一种效率较高的查找方法。

二分查找要求：线性表是有序表，即表中结点按关键字有序，并且要用向量作为表的存储结构。不妨设有序表是递增有序的。
2、基本思想

二分查找的基本思想是：

设R[low..high]是当前的查找区间

（1）首先确定该区间的中点位置：

（2）然后将待查的K值与R[mid].key比较：若相等，则查找成功并返回此位置，否则须确定新的查找区间，继续二分查找，具体方法如下：

    ①  若R[mid].key>K，则由表的有序性可知R[mid..n].keys均大于K，因此若表中存在关键字等于K的结点，则该结点必定是在位置mid左边的子表R[1..mid-1]中，故新的查找区间是左子表R[1..mid-1]。

    ②  若R[mid].key<K，则要查找的K必在mid的右子表R[mid+1..n]中，即新的查找区间是右子表R[mid+1..n]。下一次查找是针对新的查找区间进行的。

因此，从初始的查找区间R[1..n]开始，每经过一次与当前查找区间的中点位置上的结点关键字的比较，就可确定查找是否成功，不成功则当前的查找区间就缩小一半。这一过程重复直至找到关键字为K的结点，或者直至当前的查找区间为空(即查找失败)时为止。

3、存储结构

二分查找只适用顺序存储结构。

4、时间复杂度

二分查找的时间复杂度为O(log2N)

5.代码

①非递归代码
```
public static int biSearch(int []array,int a){
    int lo=0;
    int hi=array.length-1;
    int mid;
    while(lo<=hi){
        mid=(lo+hi)/2;
        if(array[mid]==a){
            return mid+1;
        }else if(array[mid]<a){
            lo=mid+1;
        }else{
            hi=mid-1;
        }
    }
    return -1;
}
```
②递归实现
```
public static int sort(int []array,int a,int lo,int hi){
    if(lo<=hi){
        int mid=(lo+hi)/2;
        if(a==array[mid]){
            return mid+1;
        }
        else if(a>array[mid]){
            return sort(array,a,mid+1,hi);
        }else{
            return sort(array,a,lo,mid-1);
        }
    }
    return -1;
}
```
