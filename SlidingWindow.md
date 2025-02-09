# 🪟 Sliding Window - Метод скользящего окна

Дан массив неотрицательных целых чисел nums и целое число k. Необходимо найти длину самого большого подмассива с суммой элементов меньшей или равной k.

```java
public int findLongestSubarray(int[] nums, int k) {
		
  int left = 0;		// левый указатель окна
  int curr = 0;		// сумма элементов окна
  int answer = 0;
		
  for (int right = 0; right < nums.length; right++) {
			
    // добавление следующего элемента массива к окну
    curr += nums[right];
			
    // до тех пор, пока окно невалидное..
    while (curr > k) {
				
      // убираем из окна элемент на месте левого указателя
      curr -= nums[left];

      // двигаем левый указатель вперед
      left++;
    }
			
    // теперь, когда окно валидное, определяем ответ
    answer = Math.max(answer, right - left + 1);
  }

  return answer;
}
```
