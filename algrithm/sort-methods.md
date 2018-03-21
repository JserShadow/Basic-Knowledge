# 常用排序方法
> 排序算法有十种：
  冒泡排序/快速排序/插入排序/选择排序/归并排序
  希尔排序/堆排序/计数排序/桶排序/基数排序
  
![sort image](./assets/sort1.png)

#### 说明:
- 稳定性：有下面的数组
```javascript
  let arrToSort = [5,3,6,6,8,0,4];
```
排序时如果数组中两个6的相对位置不变，则称这种排序算法是稳定的
- 最好情况和最坏情况：对于排序来讲，如果原数组的排序跟需求相同(根本不需要排序)的情况，称为最好情况，反之，数组排序方向与所需方向相反，则称最坏情况

## js实现上述算法(仅四种)
1. 冒泡排序：
```javascript
  function BubbleSort(arr) {
    for(let i = 0; i < arr.length - 1; i++) {
      for(let j = i + 1; j < arr.length; j++) {
        if(arr[i] > arr[j]) {
          let temp = arr[i];
          arr[i] = arr[j];
          arr[j] = temp;
        }
      }
    }
    return arr;
  }
```

2. 快速排序：
```javascript
  function QuickSort(arr) {
    if(arr.length <= 1) {
      return arr;
    }
    let standard = arr[0],
        leftArr = [],
        rightArr = [];
    for(let i = 1; i < arr.length; i++) {
      if(arr[i] >= standard) {
        rightArr.push(arr[i]);
      } else {
        leftArr.push(arr[i]);
      }
    }
    return [].concat(QuickSort(leftArr), standard, QuickSort(rightArr));
  }
```

3. 选择排序：
```javascript
  function SelectSort(arr) {
    let minIndex = 0;
    for(let i = 0; i < arr.length - 1; i++) {
      minIndex = i;
      for(let j = i + 1; j < arr.length; j++) {
        if(arr[minIndex] > arr[j]) {
          minIndex = j;
        }
      }
      if(minIndex !== i) {
        let temp = arr[minIndex];
        arr[minIndex] = arr[i];
        arr[i] = temp;
      }
    }
    return arr;
  }
```

4. 插入排序

```javascript
  function InsertSort(arr) {
    let preIndex, current;
    for(let i = 1; i < arr.length; i++) {
      preIndex = i - 1;
      current = arr[i];
      while(preIndex >= 0 && arr[preIndex] > current) {
        arr[preIndex + 1] = arr[preIndex];
        preIndex--;
      }
      arr[preIndex + 1] = current;
    }
    return arr;
  }
```