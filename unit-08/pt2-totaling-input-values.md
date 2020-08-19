# Totaling Hours and Removing Users

## Objectives
In this section we will be creating a function that allows us to sum the total hours entered for an employee and we will also create the functionality to remove a user that has been added.

In the `timesheet.component.ts` file added the following code below the `nameValidator()` custom validator that we previously created.

```
getTotalHours(employee: Employee): number {
    return employee.monday + employee.tuesday + employee.wednesday
        + employee.thursday + employee.friday + employee.saturday + employee.sunday;
}
```

![](img/total_hours_method.png)

The above `getTotalHours(employee: Employee)` function that we just created accepts an `employee` parameter which is of type `Employee`. The function will return a value in the form of a `number`. Within the actual function we are summing each day property of the employee and returning the total value.

Let's call this function in our `timesheet.component.html` and display it in the UI.

Add `<td class="total-cell">{{getTotalHours(employee)}}</td>` below the existing `<td>`

![](img/total_hours_html.png)


Also add the styling below to the `timesheet.component.scss` file to align the input values to the center.

```
.total-cell {
    text-align: center;
}
```

![](img/total_cell_scss.png)

## Acceptance Test

Run `ng serve` to start your server. Once your app is running, add an employee and start typing values into each of the hourly inputs. The `Total Hours` column on the far right should now display the total hours for each employee.

![](img/total_hours_UI.png)

