# leetcode 215. 数组中的第K个最大元素
给定整数数组 nums 和整数 k，请返回数组中第 k 个最大的元素。

请注意，你需要找的是数组排序后的第 k 个最大的元素，而不是第 k 个不同的元素。

你必须设计并实现时间复杂度为 O(n) 的算法解决此问题。


```
class  Solution {

public  int  findKthLargest(int[] arr, int  k) {

Random  rnd=new  Random();

return  sortColors(arr,0,arr.length-1,rnd,arr.length-k);

}

public  int  sortColors(int[] arr,int  l,int  r,Random  rnd,int  index)

{

int  p=Partition(arr,l,r,rnd);

if(p==index){return arr[p];}

else  if(p>index)

return  sortColors(arr,l,p-1,rnd,index);

else

return  sortColors(arr,p+1,r,rnd,index);

}

  
  

public  int  Partition(int[] arr,int  l,int  r,Random  rnd){

int  p=l+rnd.nextInt(r-l+1);

swap(arr,l,p);

int  lt=l,i=l+1,gt=r+1;

while(i<gt)

{

if(arr[i]<arr[l])

{

lt++;

swap(arr,i,lt);

i++;

}

else  if(arr[i]>arr[l])

{

gt--;

swap(arr,i,gt);

}

else

{

i++;

}

}

swap(arr,l,lt);

return lt;

  

}

public  static  void  swap(int[] arr,int  i,int  j)

{

int  t =arr[i];

arr[i]=arr[j];

arr[j]=t;

}

}
```

