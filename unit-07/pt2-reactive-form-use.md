# Reactive Form Control Use

## Introduction
Now that we've done all of the necessary setup to add an input with a reactive form control, let's add some functionality to it.

## Objectives
Our current objective is to add a plus button next to the input so that we can add the employee to a list of employees that will eventually be displayed.

The first thing that we need to do is create an `Employee` interface so that we know what kind of data were handling as our application grows and we are trying to display and work with data that is relevant to an employee.

Use the command `ng g i interfaces/employee`. This will generate an interace using the Angular CLI.

Within that `Employee` interface, add the four property definitions below.

```
id: string;
departmentId: string;
name: string;
payRate: number;
```

We will be adding more properties at a later time, but this is a good starting point.

![](img/employee_interface.png)
