Description: 
```go 
Given an array of integers, return indices of the two numbers such that they add up to a specific target.
You may assume that each input would have exactly one solution, and you may not use the same element twice. 
```

Example:
```go
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```    

Code1: 
```go 
func twoSum1(nums []int, target int) []int {
	lst := make([]int, 0)
	for i := 0; i < len(nums); i++ {
		for j := i+1; j < (len(nums)); j++ {
			if target == nums[i] + nums[j] {
				lst = append(lst, i, j)
			}
		}
	}
	return lst
}
```

Code2: 
```go 
func twoSum2(nums []int, target int) []int {
	dict := make(map[int]int, len(nums))
	for i, num := range nums {
		dict[num] = i
	}

	// dict: [3:1]

	for i, num := range nums {
		pair := target - num
		if j, ok := dict[pair]; ok && i != j {
			return []int{i, j}
		}
	}
	return nil
}
```

Code3: 
```go
func twoSum(nums []int, target int) []int {
	dict := make(map[int]int, len(nums))
	for i, num := range nums {
		pair := target - num
		if j, ok := dict[pair]; ok && i != j {
			return []int{j, i} // 注意返回值顺序，向后遍历 nums，所以 i 在 j 后
		}
		dict[num] = i
	}
	return nil
}
```
