# Round-Integer-Division 整數除法 數值簡化

There are different situations of interger division for C++ and Python. How to implement round up/down of interger division?

C++ 和 Python 在整數除法好像會出現一些不一樣的結果？來討論看看吧~

## In Mathematics 數學上

Quotient & Remainder 商 與 餘

* ` 10 /  3 =  3 ... 1`
* ` 10 / -3 = -3 ... 1`
* `-10 /  3 = -4 ... 2`
* `-10 / -3 =  4 ... 2`

float

* ` 10 /  3 =  3.3333`
* ` 10 / -3 = -3.3333`
* `-10 /  3 = -3.3333`
* `-10 / -3 =  3.3333`

## In C++

* ` 10 /  3 =  3`
* ` 10 / -3 = -3`
* `-10 /  3 = -3`
* `-10 / -3 =  3`

(I think) C++ integer division will **round towards zero** (or say **truncate**, or **round away from infinity**)

Hence, we can infer the remainder (modulus) by the result above.

* ` 10 %  3 =  1  //  10 =  3 *  3 + 1`
* ` 10 % -3 =  1  //  10 = -3 * -3 + 1`
* `-10 %  3 = -1  // -10 =  3 * -3 - 1`
* `-10 % -3 = -1  // -10 = -3 * -3 - 1`

## In Python

* ` 10 /  3 =  3`
* ` 10 / -3 = -4`
* `-10 /  3 = -4`
* `-10 / -3 =  3`

Note: if use python3, 10/3 may get 3.3333. Hence, we should use 10//3 and get 3.0 where // means floor div

(I think) Python integer division will **round down** (or say **floor**, or **round towards negative infinity**)

Hence, we can infer the remainder (modulus) by the result above.

* ` 10 %  3 =  1  //  10 =  3 *  3 + 1`
* ` 10 % -3 = -2  //  10 = -3 * -4 - 2`
* `-10 %  3 =  2  // -10 =  3 * -4 + 2`
* `-10 % -3 = -1  // -10 = -3 * -3 - 1`

## How to Round Up by C++

If the result is positive, the integer division will round down. 

Hence, we can use `#define ROUND_UP_DIV(a,b) ((a + b - 1) / b)`

However, **overflow** may happen and makes the answer wrong.

## How to Round Down by C++

If the result is negative, the integer division will round up.

Hence, we can use `#define ROUND_DOWN_DIV(a,b) ((a - b + 1) / b)`

However, **overflow** may happen and makes the answer wrong.
