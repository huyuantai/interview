# 权限系统分类
功能权限、数据权限

# 功能权限
用户->角色->菜单

# 数据权限
最基本能查看属于“本人”的数据
“本人”的基础上+附加的权限
（如同个部门的其他数据、同个公司的其他数据、跨部门的其他数据）

#### 数据权限分类
1：所有数据；
2：所在公司及以下数据；
3：所在公司数据；
4：所在部门及以下数据；
5：所在部门数据；
8：仅本人数据；
9：自定义设置，列出组织树给选，实现跨部门操作

#### 权限数据库设计
![](/assets/quanxian.PNG)

#### 创建角色时（该数据权限只针对到行权限，没有考虑列权限）
创建角色时会给角色选择功能权限，即勾选菜单
也会选择数据权限，数据权限以下拉框选择，选择以下不同的数据范围

##### 同公司同组织下的有：
1：所有数据；
2：所在公司及以下数据；
3：所在公司数据；
4：所在部门及以下数据；
5：所在部门数据；
8：仅本人数据；
> 选择以上都是同组织下的数据，因此不用列出组织树给选 不同不猛等等




##### 跨公司跨组织有
9：按明细设置，列出组织树给选，实现跨部门操作
角色-机构 表就是保存 当创建角色 选择按明细设置时，勾选的跨部门等等
记录该角色可以跨哪些部门
当用户登录，获取对应的角色，判断该角色的数据范围（dataScope），如果是9按明细设置，则去角色-机构找该角色可以跨哪些部门

当数据数据范围（dataScope）为1、2、3、4、5、8 则是同组织的，即通过同组织树实现不同范围下的数据过滤






