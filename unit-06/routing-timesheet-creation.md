# Additional Routing Techniques

## Introduction
In the previous unit we were able to display the list of departments using `mat-card`, `mat-list`, `*ngFor`, and `{{}}` (interpolation). With that now available, we want to route to a page where we can eventually enter hours for each employee that belongs to the deparment that we clicked on. When we come to the page we clicked on, we want load data that is specific to that department depending on extra information that we will pass to the router.

Let's begin by injecting the `Router` into the constructor of our `DepartmentsComponent`. Don't forget the `import { Router } from '@angular/router';` at the top of the `DepartmentsComponent`.

![](img/router_injection.png)

Next we want to provide a way that we can functionally navigate to a different page by clicking an element in the `departments.component.html` file. Previously we used `routerLink`, but in this case we want to do it through a click event.

In the `departments.component.html` file, add the below code on the same line and directly after the `*ngFor` where we are looping through each department.

`(click)="goToDepartment(department.id)"`

![](img/click_event_html.png)

What this provides is a click event for when we click on an individual department. It will call a `goToDepartment()` function and pass in the `id` of the department as a parameter. Now that we have the click event created, we need to actually create the `goToDepartment()` function within our `departments.component.ts` file. Let's do that now. Paste the next code directly below the `ngOnInit` of the `departments.component.ts` file.

```
goToDepartment(departmentId: string): void {
    this.router.navigate(['./timesheet', {id: departmentId}]);
}
```

![](img/click_event_ts.png)

We now have a `goToDepartment()` function that is called whenever the click event within the `departments.component.html` file is triggered.

Let's dig a little deeper into what `goToDepartment()` is doing. The function requires a single parameter called `departmentId` which is of type `string`. When this function is called, it calls a `navigate` method on the router. The `navigate` method on the router accepts an array of values where the first index is the path that we want to navigate to, and the optional second index is an object where each property represents a path `param` (parameter) that will be attached to the URL that you see in the browser.

## Acceptance Test

Once you have the `goToDepartment()` function and the `(click)` event added to your code, start your app by using `ng serve` and navigate to `localhost:4200`. Click on one of the departments and pay attention to the URL at the top of the page. Do you notice that there is now an `id` param that is attached to the URL?

![](img/url_param.png)


## Display Department Depending on Route Param

