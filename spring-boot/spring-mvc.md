---
description: Thmyleaf
---

# Spring MVC

## spring mvc

* Fragment on the page : `<div th:replace="header :: myheader"></div>`
* Fragment page : `<div th:fragment="myheader">`
* Link css and js files : `<link th:href="@{/bootstrap.css}" rel="stylesheet">`
* loop over list

```html
<tr th:each="employee : ${employeeList}"> 
	<td th:text="${employee.firstName}"></td> 
	<td th:text="${employee.email}"></td> 
</tr>
```

#### Dynamic button route

```html
<a th:href="@{/showFormForUpdate/{id}(id=${employee.empId})}"> </a> 

<a th:href="@{/deleteEmpl/{id}(id=${employee.empId})}" method="DELETE"> </a> 
```

#### Route

```html
<a th:href="@{/saveEmpForm}"> </a> 
```

#### Conditional Rendering

```html
<div th:if="${true}">This Element will be visible</div>` 
```

#### Form example

```html
<form action="#" th:action="@{/updateEmployee/{id}(id=${employee.empId})}" th:object="${employee}" method="POST"> 

<div class="mb-3"> 

<input th:field="*{empId}" type="text" disabled> 

<div class="mb-3"> 

<input th:field="*{firstName}" type="text" placeholder="Enter First Name"> 

<div class="mb-3"> 

<input th:field="*{lastName}" type="text" placeholder="Enter Last Name"> 

<div class="mb-3"> 

<input th:field="*{email}" type="text" placeholder="Enter Email"> 

<button type="submit" >Update Employee</button> 
```
