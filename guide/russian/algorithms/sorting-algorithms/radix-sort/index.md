---
title: Radix Sort
localeTitle: Radix Sort
---
## Radix Sort

Предпосылки: подсчет сортировки

QuickSort, MergeSort, HeapSort - это алгоритмы сортировки на основе сравнения. CountSort не является алгоритмом, основанным на сравнении. Он имеет сложность O (n + k), где k - максимальный элемент входного массива. Таким образом, если k является O (n), CountSort становится линейной сортировкой, что лучше, чем алгоритмы сортировки на основе сравнения, которые имеют сложность времени O (nlogn). Идея состоит в том, чтобы расширить алгоритм CountSort, чтобы получить лучшую временную сложность, когда k идет O (n2). Приходит идея Radix Sort.

Алгоритм:

Для каждой цифры i, где i изменяется от младшей значащей цифры до самой значащей цифры числа Сортировка массива ввода с использованием алгоритма countsort в соответствии с i-й цифрой. Мы использовали сортировку count, потому что это стабильный вид.

Пример. Предположим, что входной массив:

10,21,17,34,44,11,654,123

На основе алгоритма мы сортируем входной массив в соответствии с его цифрой (наименьшая значащая цифра).

0: 10  
1: 21 11  
2:  
3: 123  
4: 34 44 654  
5:  
6:  
7: 17  
8:  
9:  

Таким образом, массив становится 10,21,11,123,24,44,654,17 Теперь мы будем сортировать по десятизначной цифре:

0:  
1: 10 11 17  
2: 21 123  
3: 34  
4: 44  
5: 654  
6:  
7:  
8:  
9:

Теперь массив становится следующим: 10,11,17,21,123,34,44,654 Наконец, мы сортируем по ста цифре (самая значительная цифра):

0: 010 011 017 021 034 044  
1: 123  
2:  
3:  
4:  
5:  
6: 654  
7:  
8:  
9:

Массив становится: 10,11,17,21,34,44,123,654, который сортируется. Так работает наш алгоритм.

Реализация в C:

```c
void countsort(int arr[],int n,int place){
  int i,freq[range]={0}; // range for integers is 10 as digits range from 0-9 
  int output[n];

  for(i=0;i<n;i++)
    freq[(arr[i]/place)%range]++;
 
  for(i=1;i<range;i++)
    freq[i]+=freq[i-1];
 
  for(i=n-1;i>=0;i--){
    output[freq[(arr[i]/place)%range]-1]=arr[i];
    freq[(arr[i]/place)%range]--;
  }
 
  for(i=0;i<n;i++)
    arr[i]=output[i];
}
 
void radixsort(ll arr[],int n,int maxx){ // maxx is the maximum element in the array
  int mul=1;
  while(maxx){
    countsort(arr,n,mul);
    mul*=10;
    maxx/=10;
  }
}
```

Python:

```py
def counting_sort(arr, max_value, get_index):
  counts = [0] * max_value

  # Counting - O(n)
  for a in arr:s
    counts[get_index(a)] += 1
  
  # Accumulating - O(k)
  for i, c in enumerate(counts):
    if i == 0:
      continue
    else:
      counts[i] += counts[i-1]

  # Calculating start index - O(k)
  for i, c in enumerate(counts[:-1]):
    if i == 0:
      counts[i] = 0
    counts[i+1] = c

  ret = [None] * len(arr)
  # Sorting - O(n)
  for a in arr:
    index = counts[get_index(a)]
    ret[index] = a
    counts[get_index(a)] += 1
  
  return ret
```


### Дополнительная информация

*   [Википедия](https://en.wikipedia.org/wiki/Radix_sort)
    
*   [GeeksForGeeks](http://www.geeksforgeeks.org/radix-sort/)
