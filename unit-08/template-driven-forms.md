# Template Driven Forms

## Introduction
During the previous exercise, we learned about reactive form controls using `[formControl]`. Today we will learn about template driven forms which is a separate way to track form inputs.

## Objectives
Our current objective will make it so that when the user navigates to the `./timesheet` route, the user is presented with a table that displays the days of the week along with inputs for each day per employee to enter in the amount of hours that each employee worked per day. We will also include a column on the right side of the table that totals employees hours worked during that week. Additionally we will also provide a way to remove an employee.

![](img/template_driven.png)


## Create the Table Headings
First things first, in order for us to display the days of the week at the top as column headings using an `*ngFor` instead of writing them out individually, we'll need to create a `weekdays` variable in the `TimesheetComponent`. Add the next code directly below the `employeeId` variable that we created in the `timesheet.component.ts` file.

`weekdays: string[] = ['monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday', 'sunday'];`

![](img/weekdays.png)

Next, add the following HTML below the current `mat-card` that exists in the `timesheet.component.html` file.

```
<mat-card class="hours">
    <table>
        <thead>
            <th>Name</th>
            <th *ngFor="let day of weekdays">{{day}}</th>
            <th>Total Hours</th>
            <th></th>
        </thead>
    </table>
</mat-card>
```

![](img/time_table.png)

The above code will create a `mat-card` with the beginning layout for a `table`. It includes a `thead` to show all of the column headings that we will want to show including, `Name`, `Monday`-`Sunday`, `Total Hours`, and a blank heading that will eventually be the column displaying trash can icons to remove users. Notice the `*ngFor="let day of weekdays"` in the second `th` element. This is looping through the `weekdays` variable from our `timesheet.component.ts` file and displaying each weekday.

To add some separation between the two cards that exist in the `TimesheetComponent` and to make sure that the name input takes up more space, add the scss below to the `timesheet.component.scss` file.

```
mat-form-field {
    width: calc(100% - 40px);
}

.hours {
    margin-top: 30px;
}
```

![](img/card_margin.png)


At this point you can remove the `<div>{{employees | json}}</div>` from the `timesheet.component.html`. That line was within the first `mat-card`.

## Acceptance Test

Run `ng serve` and make sure that you see the same thing as the image below when you route to the `./timesheet` page from the departments page.

![](img/timesheet_headings.png)


## Create the Table Body

Now that we have created the headings to our table, our next piece to complete is the body of the table where we display inputs for each employee for each day of the week. Before we get too far into creating the inputs, we're going to alter the `Employee` interface a little bit to help us with some two way binding that we'll be doing shortly.

Add the below properties to the `Employee` interface.

```
monday: number;
tuesday: number;
wednesday: number;
thursday: number;
friday: number;
saturday: number;
sunday: number;
```

The `employee.ts` file (`Employee` interface), should now look like the image below.

![](img/employee_updated.png)

If your server is currently running, you may have noticed that you are getting errors saying that the newly add properties for an employee are missing in the `addEmployee()` function within the `timesheet.component.ts` file. Let's update the `addEmployee()` function to populate each of those day properties on a new employee with `0`.

Replace the existing `addEmployee()` function in your `timesheet.component.ts` file with the code below.

```
addEmployee(): void {
    if (this.employeeNameFC.value) {
        this.employeeId++;

        this.employees.push({
            id: this.employeeId.toString(),
            departmentId: this.department.id,
            name: this.employeeNameFC.value,
            payRate: Math.floor(Math.random() * 50) + 50,
            monday: 0,
            tuesday: 0,
            wednesday: 0,
            thursday: 0,
            friday: 0,
            saturday: 0,
            sunday: 0
        });

        this.employeeNameFC.setValue('');
    }
}
```

![](img/add_employee_update.png)


Next, let's create the body of the table where we will be inputing employee hours. Add the next bit of html directly below the `<thead>` element in the `timesheet.component.html` file.

```
<tbody>
    <tr *ngFor="let employee of employees; let i = index">
        <td>{{employee.name}}</td>
        <td *ngFor="let day of weekdays">
            <input type="number" [id]="day" [(ngModel)]="employee[day]" class="hours-input">
        </td>
    </tr>
</tbody>
```

![](img/tbody_update.png)


Notice in the `tbody` above, we are able to display a new row for every employee that exists. For each time that we click the plus button next to the Employee Name input, a new table row should be generated. With a new row being generated, the first `<td>` is displaying the name of the employee, and the next `<td>` is actually a `*ngFor` loop where we are looping through the `weekdays` variable to display a new input for each day of the week. 

Because of the `*ngFor`, each day of the week gets its own `<input>` and with that, we are able to use `[(ngModel)]` to use two way binding to bind that day of week property from the employee to the current day's input. This is done through `[(ngModel)]="employee[day]"`. We are also using data binding with the `id` of the input to correlate the correct day to the correct input.

Lastly for this snippet of code, we have a `class="hours-input"`, but no actual stying applied for that class in the `timesheet.component.scss` file. Let's add some for the `hours-input` class and also update the `hours` class as well.

```
.hours {
    min-height: 200px;
    margin-top: 30px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}

.hours-input {
    max-width: 75px;
    margin-left: 15px;
    text-align: center;
}
```

![](img/table_style_update.png)





