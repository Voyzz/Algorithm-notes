```
* ✨ 进制转换
    * 2进制→10进制
parseInt(’11’,2) //3
    * 10进制→2进制
3.toString(2)    //‘11'
* ✨ 通过和1进行与运算，可以判断其末位是不是1
    * 1001 & 0001 = 1
    * 1110 & 0001 = 0
* ✨ 异或 ( xor )
    * x ^ 0 = x
    * x ^ x = 0 (用于去重)
* ✨ a + b = n（无进位和） + c（进位和）
    * n = a ^ b
    * c = ( a & b ) << 1
    * 直至c为0，即可得其和

```