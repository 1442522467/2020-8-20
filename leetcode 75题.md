# leetcode 75题
给定一个包含红色、白色和蓝色、共 n 个元素的数组 nums ，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。

我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。

必须在不使用库的sort函数的情况下解决这个问题。
```
class  Solution {

public  void  sortColors(int[] arr) {

Random  rnd=new  Random();

sortColors(arr,0,arr.length-1,rnd);

}

public  void  sortColors(int[] arr,int  l,int  r,Random  rnd)

{

if(l>=r){return;}

int  p=Partition(arr,l,r,rnd);

sortColors(arr,l,p-1,rnd);

sortColors(arr,p+1,r,rnd);

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

