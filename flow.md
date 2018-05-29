###流程图
```flow
st=>start: 消息文本
e=>end: 消息入库
op=>operation: 跳过此条信息
op1=>operation: 去除编号中的空格、中划线
op2=>operation: 获取匹配到的关键词当做标题
op3=>operation: 真正商机
op4=>operation: 普通商机
cond1=>condition: 不包含要删除的关键词?
cond2=>condition: 不包含7位以上的字母?
cond3=>condition: 匹配7到13位字母/数字/空格/中划线?
cond4=>condition: 匹配谁有关键词
cond5=>condition: 匹配配件名称关键词
cond6=>condition: 数据库中的配件编号比较
cond7=>condition: 取编号前4位与区号对比
st->cond1->cond2->cond3(no)->cond4(no)->cond5->e
cond1(no)->op
cond1(yes)->cond2
cond2(no)->op
cond2(yes)->cond3
cond3(yes,right)->cond7
cond6(yes)->op3->op2->e
cond6(no)->op4->op2->e
cond7(yes)->op
cond7(no)->cond6
cond3(no)->cond4
cond4(yes,right)->op2->e
cond4(no)->cond5
cond5(yes)->op2->e
cond5(no)->op
```