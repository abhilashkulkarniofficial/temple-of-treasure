# [690. Employee Importance](https://leetcode.com/problems/employee-importance/)

## Solution

### Solution 1

```
let visitedEmployee = {}

function traverse(employee, employees){
    visitedEmployee[employee.id] = true
    let subordinates = employee.subordinates
    
    if(!subordinates.length){
        return employee.importance
    }
    
    let sum = 0
    
    for(let i=0; i<subordinates.length; i++){
        if(!visitedEmployee[subordinates[i].id]){
            sum += traverse(employees[subordinates[i]], employees)
        }
        
    }
    
    return sum + employee.importance
}

function parseEmployeesList(employees){
    let empObj = {}
    for(let i=0; i<employees.length; i++){
        empObj[employees[i].id] = employees[i]
    }
    return empObj
}

var GetImportance = function(employees, id) {
    employees = parseEmployeesList(employees)
    visitedEmployee = {}
    return traverse(employees[id], employees)
};
```