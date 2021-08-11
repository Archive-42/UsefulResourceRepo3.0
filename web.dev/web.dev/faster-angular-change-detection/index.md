<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format" alt="An array of light bulbs with a single bulb turned on." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/gzvMgZD2uXO7L49EWuIV.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#optimize-angular&#39;s-change-detection" class="w-toc__header--link">Optimize Angular's change detection</a>
----------------------------------------------------------------------------------------------------------------------

-   [Inside Angular's change detection](#inside-angular's-change-detection)
-   [Skipping component subtrees](#skipping-component-subtrees)
-   [Using pure pipes](#using-pure-pipes)
-   [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Optimize Angular's change detection
===================================

Implement faster change detection for better user experience.

Jul 9, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/angular" class="w-post-signpost__link">Angular</a>

[<img src="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Minko Gechev" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mgechev/)

<a href="/authors/mgechev/" class="w-author__name-link">Minko Gechev</a>

-   <a href="https://twitter.com/mgechev" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mgechev" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@mgechev" class="w-author__link">Glitch</a>
-   <a href="https://blog.mgechev.com/" class="w-author__link">Blog</a>

Angular runs its [change detection mechanism](https://angular.io/api/core/ChangeDetectorRef) periodically so that changes to the data model are reflected in an app's view. Change detection can be triggered either manually or through an asynchronous event (for example, a user interaction or an XHR completion).

Change detection is a powerful tool, but if it's run very often, it can trigger a lot of computations and block the main browser thread.

In this post you'll learn how to control and optimize the change detection mechanism by skipping parts of your application and running change detection only when necessary.

Inside Angular's change detection <a href="#inside-angular&#39;s-change-detection" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------

To understand how Angular's change detection works, let's look at a sample app!

*You can find the code for the app in [this GitHub repository](https://github.com/mgechev/change-detection-web-dev).*

The app lists employees from two departments in a company—sales and R&D—and has two components:

-   `AppComponent`, which is the root component of the app, and
-   Two instances of `EmployeeListComponent`, one for sales and one for R&D.

<img src="https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format" alt="Sample application" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/JtDFr3VL1e2AyUvhbKVU.png?auto=format&amp;w=1600 1600w" width="800" height="456" />

You can see the two instances of `EmployeeListComponent` in the template for `AppComponent`:

    <app-employee-list
      [data]="salesList"
      department="Sales"
      (add)="add(salesList, $event)"
      (remove)="remove(salesList, $event)"
    ></app-employee-list>

    <app-employee-list
      [data]="rndList"
      department="R&D"
      (add)="add(rndList, $event)"
      (remove)="remove(rndList, $event)"
    ></app-employee-list>

For each employee there's a name and a numeric value. The app passes the employee's numeric value to a business calculation and visualizes the result on screen.

For simplicity, the app is using an inefficient version of the [fibonacci function](https://en.wikipedia.org/wiki/Fibonacci_number) as its calculation to show the implications of heavy bindings in an app.

Now take a look at `EmployeeListComponent`:

    const fibonacci = (num: number): number => {
      if (num === 1 || num === 2) {
        return 1;
      }
      return fibonacci(num - 1) + fibonacci(num - 2);
    };

    @Component(...)
    export class EmployeeListComponent {
      @Input() data: EmployeeData[];
      @Input() department: string;
      @Output() remove = new EventEmitter<EmployeeData>();
      @Output() add = new EventEmitter<string>();

      label: string;

      handleKey(event: any) {
        if (event.keyCode === 13) {
          this.add.emit(this.label);
          this.label = '';
        }
      }

      calculate(num: number) {
        return fibonacci(num);
      }
    }

`EmployeeListComponent` accepts a list of employees and a department name as inputs. When the user tries to remove or add an employee, the component triggers a corresponding output. The component also defines the `calculate` method, which implements the business calculation.

Here's the template for `EmployeeListComponent`:

    <h1 title="Department">{{ department }}</h1>
    <mat-form-field>
      <input placeholder="Enter name here" matInput type="text" [(ngModel)]="label" (keydown)="handleKey($event)">
    </mat-form-field>
    <mat-list>
      <mat-list-item *ngFor="let item of data">
        <h3 matLine title="Name">
          {{ item.label }}
        </h3>
        <md-chip title="Score" class="mat-chip mat-primary mat-chip-selected" color="primary" selected="true">
          {{ calculate(item.num) }}
        </md-chip>
      </mat-list-item>
    </mat-list>

This code iterates over all the employees in the list and, for each one, renders a list item. It also includes an `ngModel` directive for two-way data binding between the input and the `label` property declared in `EmployeeListComponent`.

With the two instances of `EmployeeListComponent`, the app forms the following component tree:

<img src="https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format" alt="Component tree" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/iMfgq2xaKVRcXc3LhWW7.png?auto=format&amp;w=1600 1600w" width="800" height="454" />

`AppComponent` is the root component of the application. Its child components are the two instances of `EmployeeListComponent`. Each instance has a list of items (E<sub>1</sub>, E<sub>2</sub>, etc.) that represent the individual employees in the department.

When the user begins entering the name of a new employee in the input box in an`EmployeeListComponent`, Angular triggers change detection for the entire component tree starting from `AppComponent`. This means that while the user is typing in the text input, Angular is repeatedly recalculating the numeric values associated with each employee to verify that they haven't changed since the last check.

To see how slow this can be, open the [non-optimized version of the project on StackBlitz](https://stackblitz.com/github/mgechev/change-detection-web-dev) and try entering an employee name.

You can verify that the slowdown comes from the `fibonacci` function by setting up the [example project](https://github.com/mgechev/change-detection-web-dev) and opening the **Performance** tab of Chrome DevTools.

1.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
2.  Click the **Performance** tab.

Now click **Record** <span style="width: 13px;height: 13px;background-color: #6E6E6E;display: inline-block;border-radius: 50%;margin-left: 3px;margin-right: 3px;"></span> (in the top-left corner of the **Performance** panel) and start typing in one of the text boxes in the app. In a few seconds, click **Record** <span style="width: 13px;height: 13px;background-color: #6E6E6E;display: inline-block;border-radius: 50%;margin-left: 3px;margin-right: 3px;"></span> again to stop recording. Once Chrome DevTools processes all the profiling data it collected, you'll see something like this:

<img src="https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format" alt="Performance profiling" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/1rXcCcnM7rLj183jgQCk.png?auto=format&amp;w=1600 1600w" width="800" height="276" />

If there are many employees in the list, this process may block the browser's UI thread and cause frame drops, which leads to a bad user experience.

Skipping component subtrees <a href="#skipping-component-subtrees" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------

When the user is typing in the text input for the *sales* `EmployeeListComponent` you know that the data in the *R&D* department isn't changing—so there's no reason to run change detection on its component. To make sure the R&D instance doesn't trigger change detection, set the `changeDetectionStrategy` of `EmployeeListComponent` to `OnPush`:

    import { ChangeDetectionStrategy, ... } from '@angular/core';

    @Component({
      selector: 'app-employee-list',
      template: `...`,
      changeDetection: ChangeDetectionStrategy.OnPush,
      styleUrls: ['employee-list.component.css']
    })
    export class EmployeeListComponent {...}

Now when the user types in a text input, change detection is only triggered for the corresponding department:

<img src="https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format" alt="Change detection in a component subtree" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/1hUupNUByRDQLyYYvMcX.png?auto=format&amp;w=1600 1600w" width="800" height="462" />

*You can find this optimization applied to the original application [here](https://github.com/mgechev/change-detection-web-dev/tree/onpush).*

You can read more about the `OnPush` change detection strategy in the [official Angular documentation](https://angular.io/api/core/ChangeDetectionStrategy).

To see the effect of this optimization, enter a new employee in the [application on StackBlitz](https://stackblitz.com/github/mgechev/change-detection-web-dev/tree/onpush).

Using pure pipes <a href="#using-pure-pipes" class="w-headline-link">#</a>
--------------------------------------------------------------------------

Even though the change detection strategy for the `EmployeeListComponent` is now set to `OnPush`, Angular still recalculates the numeric value for all employees in a department when the user types in the corresponding text input.

To improve this behavior you can take advantage of [pure pipes](https://angular.io/guide/pipes#pure-and-impure-pipes). Both pure and impure pipes accept inputs and return results that can be used in a template. The difference between the two is that a pure pipe will recalculate its result only if it receives a different input from its previous invocation.

Remember that the app calculates a value to display based on the employee's numeric value, invoking the `calculate` method defined in `EmployeeListComponent`. If you move the calculation to a pure pipe, Angular will recalculate the pipe expression only when its arguments change. The framework will determine if the arguments of the pipe have changed by performing a reference check. This means that Angular won't perform any recalculations unless the numeric value for an employee is updated.

Here's how to move the business calculation to a pipe called `CalculatePipe`:

    import { Pipe, PipeTransform } from '@angular/core';

    const fibonacci = (num: number): number => {
      if (num === 1 || num === 2) {
        return 1;
      }
      return fibonacci(num - 1) + fibonacci(num - 2);
    };

    @Pipe({
      name: 'calculate'
    })
    export class CalculatePipe implements PipeTransform {
      transform(val: number) {
        return fibonacci(val);
      }
    }

The `transform` method of the pipe invokes the `fibonacci` function. Notice that the pipe is pure. Angular will consider all pipes pure unless you specify otherwise.

Finally, update the expression inside of the template for `EmployeeListComponent`:

    <mat-chip-list>
      <md-chip>
        {{ item.num | calculate }}
      </md-chip>
    </mat-chip-list>

That's it! Now when the user types in the text input associated with any department, the app won't recalculate the numeric value for individual employees.

In the app below you can see how much smoother the typing is!

To see the effect of the last optimization [try this example on StackBlitz](https://stackblitz.com/github/mgechev/change-detection-web-dev/tree/pure-pipe).

*The code with the pure pipe optimization of the original application is available [here](https://github.com/mgechev/change-detection-web-dev/tree/pure-pipe).*

Conclusion <a href="#conclusion" class="w-headline-link">#</a>
--------------------------------------------------------------

When facing runtime slowdowns in an Angular app:

1.  Profile the application with Chrome DevTools to see where the slowdowns are coming from.
2.  Introduce the `OnPush` change detection strategy to prune a component's subtrees.
3.  Move heavy computations to pure pipes to allow the framework to perform caching of the computed values.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jul 9, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/angular/faster-angular-change-detection/index.md)

<a href="/angular" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

-   ### Contribute

    -   <a href="https://github.com/GoogleChrome/web.dev/issues/new?assignees=&amp;labels=bug&amp;template=bug_report.md&amp;title=" class="w-footer__linkbox-link">File a bug</a>
    -   <a href="https://github.com/googlechrome/web.dev" class="w-footer__linkbox-link">View source</a>

-   ### Related content

    -   <a href="https://blog.chromium.org/" class="w-footer__linkbox-link">Chrome updates</a>
    -   <a href="https://developers.google.com/web/" class="w-footer__linkbox-link">Web Fundamentals</a>
    -   <a href="https://developers.google.com/web/showcase/" class="w-footer__linkbox-link">Case studies</a>
    -   <a href="https://devwebfeed.appspot.com/" class="w-footer__linkbox-link">DevWeb Content Firehose</a>
    -   <a href="/podcasts/" class="w-footer__linkbox-link">Podcasts</a>
    -   <a href="/shows/" class="w-footer__linkbox-link">Shows</a>

-   ### Connect

    -   <a href="https://www.twitter.com/ChromiumDev" class="w-footer__linkbox-link">Twitter</a>
    -   <a href="https://www.youtube.com/user/ChromeDevelopers" class="w-footer__linkbox-link">YouTube</a>

<a href="https://developers.google.com/" class="w-footer__utility-logo-link"><img src="/images/lockup-color.png" alt="Google Developers" class="w-footer__utility-logo" width="185" height="33" /></a>

-   <a href="https://developer.chrome.com/" class="w-footer__utility-link">Chrome</a>
-   <a href="https://firebase.google.com/" class="w-footer__utility-link">Firebase</a>
-   <a href="https://cloud.google.com/" class="w-footer__utility-link">Google Cloud Platform</a>
-   <a href="https://developers.google.com/products" class="w-footer__utility-link">All products</a>

<!-- -->

-   <a href="https://policies.google.com/" class="w-footer__utility-link">Terms &amp; Privacy</a>
-   <a href="/community-guidelines/" class="w-footer__utility-link">Community Guidelines</a>

Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/terms/site-policies).
