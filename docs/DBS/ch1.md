# Lecture 1: Introduction 
> 以概要为主,总览一下本学期的内容

## 1.1 Purpose of Database Systems

- `file-processing system`是传统操作系统所支持的:

!!! note "可能存在的问题"
    - Data **redundancy（数据冗余）** and **inconsistency（不一致）:**
       > Multiple file formats, duplication of information in different files.
       > 相同的信息可能在不同的文件中多次出现，并且可能导致数据的不一致。
    
    - Data  **isolation(数据孤立，数据孤岛)**:
       > multiple files and formats
       > 数据之间没有关联，职能通过程序连接

    - Difficulty in **accessing data** （存取数据困难）:
       > Need to write a new program to carry out each new task

    - **完整性问题（integrity problem）**:
       > 数据库中所存储的数据值必须满足某些特定类型的完整性约束 （ consistency constraint ） 

    - **Atomicity problems（原子性问题）**:
       >  两个（或以上）的操作必须同时发生，作为一个整体

    - **Concurrent access anomalies（并发访问异常）**

    - **Security problems（安全性问题） **

通过**Database Systems**我们可以解决上面出现的问题

## 1.2 Characteristics of Databases

- 一些基本特性：
  
!!! success "Characteristics of Databases"
    - data persistence(数据持久性)
    - convenience in accessing data(数据访问便利性)
    - data integrity （数据完整性）
    - concurrency control for multiple user(多用户并发控制)
    - failure recovery（故障恢复） 
    - security  control（安全控制）



- View of Data:

!!! note "Three-level abstraction of databases"
    - **view level** -> view schema
    - **logical level** -> logical schema 
    - **physical level** -> physical 
    !!! tip "物理数据独立性"
        通过逻辑层可以实现物理数据的独立性(**physical data independence**)


!!! tip "Schema and Instance "
    模式和实例，可以理解为 OOP 中的 class 和 object
       

!!! note "Data Independence"
    - **Physical Data Independence（物理数据独立性）**
        - the ability to modify the physical schema without changing the logical schema
        - 物理层的改变不影响逻辑层
        > 类比于 OOP 中只对接口进行提供
    
    - **Logical Data Independence(逻辑数据独立性)**
        - 逻辑层的改变不影响视图层
        -  the ability to modify the logical schema without changing the user view schema


## 1.3 Data Models 
> 数据模型：Database的基础

- A collection of tools for describing 
    - Data (数据)
    - Data relationships(联系)
    - Data semantics(语义)
    - Data constraints(约束)
- Relational model(关系模型)
- Entity-Relationship(实体-联系) data model 
- Object-based data models 
    - Object-oriented  (面向对象数据模型)
    - Object-relational(对象-关系模型模型)
- Semistructured data model  (XML)(半结构化数据模型)
- Other older models:
    - Network model  (网状模型)
    - Hierarchical model(层次模型)


## 1.4 Database Language

!!! note "一些术语"
    - **DDL**: Data Define Language 
    - **DML**: Data Manipulation Language 
    - **SQL Query Language**
    - **Application Program Interface （API）**


## 1.5 Database Design(数据库设计)

!!! success "两个核心内容"
    - Database Design(数据库设计) Chapter 7 
    - Normalization Theory（规范化理论） (Chapter 8)
      > 如何设计更高效，更简单，能够解决 1.1 中存在的问题 



## 1.6 Database Engine 
> 数据库引擎 -> 夏学期重点

!!! note "几个功能模块"
    - The **storage manager**
    - The  **query processor** component
    - The **transaction（事物管理） management** component.

## 1.7 Database Users 

- naive users 
- application users 
- sophisticated users 

!!! tips "DBA"
    **DataBase Administrator** (数据库管理员)