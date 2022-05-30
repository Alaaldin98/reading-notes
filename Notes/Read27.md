## Views in ASP.NET Core MVC
### Benefits of using views
Views help to establish separation of concerns within an MVC app by separating the user interface markup from other parts of the app. Following SoC design makes your app modular, which provides several benefits:

- The app is easier to maintain because it's better organized. Views are generally grouped by app feature. This makes it easier to find related views when working on a feature.
- The parts of the app are loosely coupled. You can build and update the app's views separately from the business logic and data access components. You can modify the views of the app without necessarily having to update other parts of the app.
- It's easier to test the user interface parts of the app because the views are separate units.
- Due to better organization, it's less likely that you'll accidentally repeat sections of the user interface.

### How controllers specify views
Views are typically returned from actions as a ViewResult, which is a type of ActionResult. Your action method can create and return a ViewResult directly, but that isn't commonly done. Since most controllers inherit from Controller, you simply use the View helper method to return the ViewResult

### View discovery
When an action returns a view, a process called view discovery takes place. This process determines which view file is used based on the view name

### Pass data to views
> Pass data to views using several approaches:

- Strongly typed data: viewmodel
- Weakly typed data
  - ViewData (ViewDataAttribute)
  - ViewBag
### Strongly-typed data (viewmodel)
The most robust approach is to specify a model type in the view. This model is commonly referred to as a viewmodel. You pass an instance of the viewmodel type to the view from the action.


### Summary of the differences between ViewData and ViewBag
ViewBag isn't available by default for use in Razor Pages PageModel classes.

- ViewData
  - Derives from ViewDataDictionary, so it has dictionary properties that can be useful, such as ContainsKey, Add, Remove, and Clear.
  - Keys in the dictionary are strings, so whitespace is allowed. Example: ViewData["Some Key With Whitespace"]
  - Any type other than a string must be cast in the view to use ViewData.
- ViewBag
  - Derives from Microsoft.AspNetCore.Mvc.ViewFeatures.Internal.DynamicViewData, so it allows the creation of dynamic properties using dot notation (@ViewBag.SomeKey = <value or object>), and no casting is required. The syntax of ViewBag makes it quicker to add to controllers and views.
  - Simpler to check for null values. Example: @ViewBag.Person?.Name

## Ways To Create Form In ASP.NET MVC
