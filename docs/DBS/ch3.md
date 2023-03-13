# Chapter3 Introduction to SQL
> 本章主要介绍一些基本的 **SQL** 语句


## DDL (Data Definition Language)
!!! note "DDL (Data Definition Language)"
    - ![](../img/DBS/ch3/1.png)

!!! note "数据类型"
    - ![](../img/DBS/ch3/2.png)
    - ![](../img/DBS/ch3/3.png)

!!! note "Create Table"
    - ![](../img/DBS/ch3/4.png)

    !!! success "Integrity Constraints(完整性约束条件)"
        - **not null**
        - **primary key** ($A_1, A_2... A_n$)
        - **foreign key** ($A_1, A_2... A_n$) references r
        - ![](../img/DBS/ch3/5.png)
        - 在删除/更新 **foreign key** 时，我们可能会对原有的结构造成破坏，我们有如下解决方案：
            - 相应的删除/更新指向他的foreign key 
            - set null 
            - 限制这种操作的进行
            - set default  
        - ![](../img/DBS/ch3/6.png)


!!! note "Drop and Alter"
    - ![](../img/DBS/ch3/7.png)


## DML: data-manipulation language 

!!! note "基本形式"
    - ![](../img/DBS/ch3/8.png)


!!! note "distinct/all"
    - **distinct**: 增加多重集的去重操作，筛选出的内容不会重复
    - **all**: 把所有的结果都选择出来
    - ![](../img/DBS/ch3/9.png)

!!! note "其他形式"
    - `select *`: 可以将全部的项选择出来
    - **select** 后可以加入代数运算
    - **where** 后的选择条件可以使用 **and**, **or**, **not** 等逻辑运算
    - **where** 后可以使用 **between... and...** 进行连接
    - **where** 后支持 **tuple**的比较


!!! note "joins"
    - ![](../img/DBS/ch3/10.png)
    - ![](../img/DBS/ch3/11.png)
    - **natural join** 有时可能会存在一些问题，需要我们灵活使用
        - ![](../img/DBS/ch3/12.png) 
    - 我们可以使用 **using** 运算符来进行 join 
        - ![](../img/DBS/ch3/13.png) 

!!! note "as"
    - 使用 **as** 我们可以进行重命名

!!! note "String Operation"
    - ![](../img/DBS/ch3/14.png) 
    - ![](../img/DBS/ch3/15.png) 

!!! note "Order"
    - ![](../img/DBS/ch3/16.png) 
    - ![](../img/DBS/ch3/17.png) 


!!! note "Set Operation"
    - **union**, **intersect** , **except**: 分别对应集合运算 $\cup$, $\cap$ , $-$ 。这三个操作会帮我们自动除去重复的项，多重集相同的项出现多次我们只保留一个。
    - 如果我们想要保留多重集的重复部分可以使用：**union all**, **intersect all** , **except all**
    
    
!!! note "Aggregate Functions"
    - 我们可以使用的聚合函数包括： **avg, min, max, sum, count**
    - ![](../img/DBS/ch3/18.png)
    !!! success "group by " 
        - ![](../img/DBS/ch3/19.png)
        - 要注意的是，如果我们在 select 后使用了聚合函数后，那么在 select 后面的属性如果不是聚合函数的参数，那么它一定要出现在 **group by** 中，否则我们的操作便是错误的。
        - ![](../img/DBS/ch3/20.png)

    !!! success "having"
        - 通过 **having** 我们可以将过滤得到的表在此进行**行方向**的再一步筛选
        - ![](../img/DBS/ch3/21.png)


!!! note "Nested Subqueries(嵌套子查询)"
    - 类似于**二重循环**
    - 通过 **in** , **not in**
    - **some**, **all** 关键词可以在比较运算时进行使用
    - 子查询返回的是单个的值可以不指定 **some**/**all**
    - **exists** , **not exists**: 判断筛选出来的子查询是否为空。
    - 一个例子：![](../img/DBS/ch3/22.png)
    - **unique**: 不是多重集，没有重复的元组，但是可以为空。
    - **with**: 可以讲子查询重新命名，尽量不要使用。

!!! note "Modification of the Database"
    - **deletion**: ![](../img/DBS/ch3/23.png)
    ![](../img/DBS/ch3/24.png) 

    - **insert**: ![](../img/DBS/ch3/25.png)
    - ![](../img/DBS/ch3/26.png)
    
    - **updates**: ![](../img/DBS/ch3/27.png)
    - ![](../img/DBS/ch3/28.png)
    - ![](../img/DBS/ch3/29.png)