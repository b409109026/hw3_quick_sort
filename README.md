# hw3_quick_sort
def quick_sort(arr, start, end):
    #檢查陣列長度，如果為1，則返回陣列
    if start >= end:
        return 

    #左指標指向第一個元素，右指標指向最後一個元素
    pivot = arr[start]
    left = start
    right = end

    #檢查左右指標的值，大於基準的放右邊，小於基準的放左邊
    while left < right:
        while arr[right] >= pivot and right > left:
            right -= 1
        while arr[left] <= pivot and left < right:
            left += 1
        if left < right:
            arr[left], arr[right] = arr[right], arr[left]

    #將基準移到中間
    arr[start], arr[left] = arr[left], arr[start]

    #遞迴排序左右子序列
    quick_sort(arr, start, left - 1)
    quick_sort(arr, left + 1, end)

    return arr

#測試講義中的範例
arr = [3, 25, 8, 13, 33, 119, 54, 84, 67, 41]
quick_sort(arr, 0, len(arr) - 1)
print(arr)
