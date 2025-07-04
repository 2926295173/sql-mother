# 查询进阶 - 关联查询 - cross join


## 教程
在之前的教程中，我们所有的查询操作都是在单个数据表中进行的。但有时，我们可能希望在单张表的基础上，获取更多额外数据，比如获取学生表中学生所属的班级信息等。这时，就需要使用关联查询。

在 SQL 中，关联查询是一种用于联合多个数据表中的数据的查询方式。

其中，`CROSS JOIN` 是一种简单的关联查询，不需要任何条件来匹配行，它直接将左表的 **每一行** 与右表的 **每一行** 进行组合，返回的结果是两个表的笛卡尔积。



## 示例
假设有一个员工表 `employees`，包含以下字段：`emp_id`（员工编号）、`emp_name`（员工姓名）、`department`（所属部门）、`salary`（工资）。数据如下：

| emp_id | emp_name | department | salary |
|--------|----------|------------|--------|
| 1      | 小明     | 技术部     | 5000   |
| 2      | 鸡哥     | 财务部     | 6000   |
| 3      | 李华     | 销售部     | 4500   |



假设还有一个部门表 `departments`，包含以下字段：`department`（部门名称）、`manager`（部门经理）、`location`（所在地）。数据如下：

| department | manager | location |
|------------|---------|----------|
| 技术部     | 张三    | 上海     |
| 财务部     | 李四    | 北京     |
| 销售部     | 王五    | 广州     |



使用 CROSS JOIN 进行关联查询，将员工表和部门表的所有行组合在一起，获取员工姓名、工资、部门名称和部门经理，示例 SQL 代码如下：

```sql
SELECT e.emp_name, e.salary, d.department, d.manager
FROM employees e
CROSS JOIN departments d;
```

上面的 SQL 还可以简化为：

```sql
SELECT e.emp_name, e.salary, d.department, d.manager
FROM employees e, departments d;
```

通过逗号分隔表名，隐式地实现了笛卡尔积，是 SQL 早期的写法，功能上与 CROSS JOIN 完全相同。

注意，在多表关联查询的 SQL 中，我们最好在选择字段时指定字段所属表的名称（比如 e.emp_name），还可以通过给表起别名（比如 employees e）来简化 SQL 语句。

查询结果：

| emp_name | salary | department | manager |
|----------|--------|------------|---------|
| 小明     | 5000   | 技术部     | 张三    |
| 小明     | 5000   | 财务部     | 李四    |
| 小明     | 5000   | 销售部     | 王五    |
| 鸡哥     | 6000   | 技术部     | 张三    |
| 鸡哥     | 6000   | 财务部     | 李四    |
| 鸡哥     | 6000   | 销售部     | 王五    |
| 李华     | 4500   | 技术部     | 张三    |
| 李华     | 4500   | 财务部     | 李四    |
| 李华     | 4500   | 销售部     | 王五    |



## 题目

假设有一个学生表 `student` ，包含以下字段：id（学号）、name（姓名）、age（年龄）、class_id（班级编号）；还有一个班级表 `class` ，包含以下字段：id（班级编号）、name（班级名称）。

请你编写一个 SQL 查询，将学生表和班级表的所有行组合在一起，并返回学生姓名（student_name）、学生年龄（student_age）、班级编号（class_id）以及班级名称（class_name）。
