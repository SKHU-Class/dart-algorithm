## Description

주어진 배열(nums)에서 두 값을 뽑아 그 합이 타겟(target)이 되도록하는 두 값의 인덱스를 배열로 반환하라

## Example

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

## Solution

### 1번 풀이 **827 ms**

- Brute Force 식 풀이

```dart
class Solution {
  List<int> twoSum(List<int> nums, int target) {
    for (int i = 0; i < nums.length; i++) {
      for (int j = i + 1; j < nums.length; j++) {
        if (nums[i] + nums[j] == target) {
          return [i, j];
        }
      }
    }
    return [];
  }
}
```

### 2번 풀이 **428 ms**

- 먼저 Map을 하나 만든다.
- nums를 반복하며 `target - nums의 원소`가 Map에 있는 지 검사.
- 없다면 nums의 원소를 Map에 넣음.
- 있다면 정답 반환.

```dart
class Solution {
  List<int> twoSum(List<int> nums, int target) {
    Map<int, int> items = {};
    for (int i = 0; i < nums.length; i++) {
      num x = target - nums[i];
      if (items.containsKey(x)) {
        return [items[x]!, i];
      }
      items[nums[i]] = i;
    }
    return [];
  }
}
```
