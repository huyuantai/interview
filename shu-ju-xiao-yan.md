单条记录

# 多个记录列表
1.列表内校验重复，如联考时 可能选择了两个科目一，这时要判断是否包含了两个科目一，包含提示重复

2.新增时只允许存在一条，那么新增时要判断是否已存在
如拨款时，同个驾培申请记录id只允许一条拨款记录，那么新增拨款记录 要先通过驾培申请记录id 检查是否已有 拨款记录，有则提示重复

3.新增、编辑 各类信息重复检验，如备案号不能一样

4.必填参数的校验

5.手机、身份证、车牌号、邮箱等正则校验

6.要使用时的字段的校验，如传递的Id，从数据库拿回来的数据

7.树形结构要校验环形结构，避免成环形结构