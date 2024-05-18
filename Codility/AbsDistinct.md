# Question description

---

A non-empty array A consisting of N numbers is given. The array is sorted in non-decreasing order. The absolute distinct count of this array is the number of distinct absolute values among the elements of the array.

For example, consider array A such that:

  A[0] = -5
  A[1] = -3
  A[2] = -1
  A[3] =  0
  A[4] =  3
  A[5] =  6
The absolute distinct count of this array is 5, because there are 5 distinct absolute values among the elements of this array, namely 0, 1, 3, 5 and 6.

Write a function:

function solution(A);

that, given a non-empty array A consisting of N numbers, returns absolute distinct count of array A.

For example, given array A such that:

  A[0] = -5
  A[1] = -3
  A[2] = -1
  A[3] =  0
  A[4] =  3
  A[5] =  6
the function should return 5, as explained above.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [1..100,000];
each element of array A is an integer within the range [−2,147,483,648..2,147,483,647];
array A is sorted in non-decreasing order.

---

### My interpretation
This is asking from the array of numbers retrieve the amount of absolute unique distinct values.

#### Examples

`test([-1,1,2,3,4,5])`

Will return `5` because once you remove all negative symbols and then check for unique values there are: `1,2,3,4,5` so `5` is returned.

---

`test([-1,0,0,0,1])`

Will return `2` because once you remove all negative symbols and then check for unique values there are: `0,1` so `2` is returned.

---

`test([-5,-3,-2,-1,1,2])`

Will return `4` because once you remove all negative symbols and then check for unique values there are: `1,2,3,5` so `4` is returned.

---

### My solution (18th May 2024 14:00:14)

- We use a Javascript `set` to help get a unique set of numbers.
- Loop through the array and check if the set has that absolute number, if it doesn't then add it to the set.
- We return the size of the set which will give us the absolute unique distinct values.

```
function test(A) {
    let set = new Set();
    A.forEach((value, index) => {
        if (!set.has(Math.abs(value))) {
            set.add(Math.abs(value))
        }
    })

    return set.size
}
```