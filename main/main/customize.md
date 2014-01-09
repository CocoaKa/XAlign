
如何自定义pattern

我们以 @property 为例

首先分段，主要就是和空格打交道

```
1. ^\s*@property\s*  // 要把 property与后面的( 之间的空白 换成一个 ' '
   ^\s*@property\s* => @property空格
   
   像这一种匹配上的，我们叫match，

2. \(.*\)\s* 括号内的不处理，直接全部拿下，记得带上小弟\s*，也要有个空格
   
   \(.*\)\s* =》  [\1.tailTrim paddingTo:MAX( \1.tailTrim )]

3. 问题少年来了
   我们能确定的是类型和变量之间分隔符，规则是 [\s\*]+(?=\w+;) 
   这个match把剩余的字符串分为了两部分，我们称为 head 和 tail;
   我们期望的对齐方式是
   1. head 最大，
   2. match 看个人喜好，反正 * 是批匹出来，没*记得的要有空格。
   3. tail 其实我们控制不了，除非他是最后一个，因为它的位置是根据前面算出来的


