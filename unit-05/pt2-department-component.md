# Department Component Creation and Service Injection

## Introduction

During the previous exercise we created the department service and populated a `departments` variable with seed data. Now that we have access to a departments service and data within it, we can create the departments component that will display the list of departments.

## Inject the Deparments Service

Within the `departments.component.ts` file constructor, let's inject the `DepartmentsService`. The constuctor within the `deparments.component.ts` file should look like the image below. Don't forget to import the `DepartmentsService` at the top of your component.

![](img/service_injection.png)

The next step before we can try and display the departments using HTML would be to create a departments variable within the `deparments.component.ts` file that is set to the same value as the departments variable within the `DeparmentsService`. Follow the next steps in order.

1. Create the departments variable in the `deparments.component.ts` file. `departments: Department[];`, don't forget the import at the top of your `departments.component.ts` file.

![](img/department_comp_variable.png)
