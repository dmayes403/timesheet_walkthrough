# Department Component Creation and Service Injection

## Introduction

During the previous exercise we created the department service and populated a `departments` variable with seed data. Now that we have access to a departments service and data within it, we can create the departments component that will display the list of departments.

## Inject the Deparments Service

Within the `departments.component.ts` file constructor, let's inject the `DepartmentsService`. The constuctor within the `deparments.component.ts` file should look like the image below. Don't forget to import the `DepartmentsService` at the top of your component.

![](img/service_injection.png)

The next step before we can try and display the departments using HTML would be to create a departments variable within the `deparments.component.ts` file that is set to the same value as the departments variable within the `DeparmentsService`. Follow the next steps in order.

1. Create the departments variable in the `deparments.component.ts` file. `departments: Department[];`, don't forget the import at the top of your `departments.component.ts` file.

![](img/department_comp_variable.png)

2. Within the `ngOnInit` life cycle hook of the `DepartmentsComponent`, set the `departments` variable equal to the `departments` variable from the `DepartmentsService`.

```
ngOnInit(): void {
    this.departments = this.departmentsService.departments;
}
```

![](img/set_departments.png)

Now that we have set the `departments` variable within the `DepartmentsComponent` we can display each of the departments using HTML. Paste the below code into your `departments.component.html` file.

```
<div class="main-container">
    <mat-card>
        <mat-list>
            <mat-list-item *ngFor="let department of departments">
                {{department.name}}
            </mat-list-item>
        </mat-list>
    </mat-card>
</div>
```

Run `ng serve` and see if your app runs without errors.

At this point you should see multiple errors logging in your terminal. A couple of them should relate to `mat-card` and `mat-list`. That is because both `mat-card` and `mat-list` are Angular Material compnents that require imports into our `material.module.ts` module.

Import both `https://material.angular.io/components/card/api` and `https://material.angular.io/components/list/api` into the `material.module.ts` file in the same way that we did the imports for the `mat-toolbar`

Your `MaterialModule` should look like the image below.

![](img/card_list_imports.png)

At this point you can restart your server with `ng serve` and you shouldn't see any errors.