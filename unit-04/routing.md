# Routing and Department Component Creation

## Introduction

The end goal of our application is to have three different viewable pages that we can navigate between. In order for us to do that in the form of a SPA (single page application), Angular provides a RouterModule which allows us view different components as a single page depending on which route we are navigating too. When we initialized our application, we opted to include an `AppRoutingModule`, which you can see in the `app-routing.module.ts` file. This is where we will determine our routes that are attached to certain paths (urls), and which component will be loaded per route.

## Update Routes Array

Go to the `app-routing.module.ts` file, and replace the line where it has 
`const routes: Routes[] = [];`

with
```
const routes: Routes = [
    { path: '',   redirectTo: 'departments', pathMatch: 'full' },
    { path: 'departments', component: DepartmentsComponent },
    { path: 'timesheet', component: TimesheetComponent },
    { path: 'analytics', component: AnalyticsComponent }
];
```

Remember, in the code that we just pasted, `{ path: '',   redirectTo: 'departments', pathMatch: 'full' }` is saying that when we first come to the root path of localhost:4200, we want the user to be redirected to the `departments` path so that the `DepartmentsComponent` will be displayed. All of the other paths will be loaded as we direct the user to them by other ways.

To make it so that the router works, we need to add `<router-outlet style="height: 100%;"></router-outlet>` to the `app.component.html` file.

Your `app.component.html` file should look like the image below.

![](img/router_outlet.png)


