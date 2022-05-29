##  Roles, Claims and JWT Tokens


### Adding claims checks
Claim based authorization checks:

- Are declarative.
- Are applied to Razor Pages, controllers, or actions within a controller.
- Can not be applied at the Razor Page handler level, they must be applied to the Page.

Claims in code specify claims which the current user must possess, and optionally the value the claim must hold to access the requested resource. Claims requirements are policy based, the developer must build and register a policy expressing the claims requirements.

### Add a generic claim check
If the claim value isn't a single value or a transformation is required, use RequireAssertion. For more information, see Use a func to fulfill a policy.

### Multiple Policy Evaluation
If you apply multiple policies to a controller or action, then all policies must pass before access is granted. For example:

```c#
[Authorize(Policy = "EmployeeOnly")]
public class SalaryController : Controller
{
    public IActionResult Index()
    {
        return View();
    }

    public IActionResult Payslip()
    {
        return View();
    }

    [Authorize(Policy = "HumanResources")]
    public IActionResult UpdateSalary()
    {
        return View();
    }
}
```


### The difference between Authentication and Authorisation
First of all, we should clarify the difference between these two dependent facets of security. The simple answer is that Authentication is the process of determining who you are, while Authorisation revolves around what you are allowed to do, i.e. permissions. Obviously before you can determine what a user is allowed to do, you need to know who they are, so when authorisation is required, you must also first authenticate the user in some way.

### Authentication in ASP.NET Core
The fundamental properties associated with identity have not really changed in ASP.NET Core - although they are different, they should be familiar to ASP.NET developers in general. For example, in ASP.NET 4.x, there is a property called User on HttpContext, which is of type IPrincipal, which represents the current user for a request. In ASP.NET Core there is a similar property named User, the difference being that this property is of type ClaimsPrincipal, which implements IPrincipal.










The move to use ClaimsPrincipal highlights a fundamental shift in the way authentication works in ASP.NET Core compared to ASP.NET 4.x. Previously, authorisation was typically Role-based, so a user may belong to one or more roles, and different sections of your app may require a user to have a particular role in order to access it. In ASP.NET Core this kind of role-based authorisation can still be used, but that is primarily for backward compatibility reasons. The route they really want you to take is claims-based authentication.

### Claims-based authentication
The concept of claims-based authentication can be a little confusing when you first come to it, but in practice it is probably very similar to approaches you are already using. You can think of claims as being a statement about, or a property of, a particular identity. That statement consists of a name and a value. For example you could have a DateOfBirth claim, FirstName claim, EmailAddress claim or IsVIP claim. Note that these statements are about what or who the identity is, not what they can do.






The identity itself represents a single declaration that may have many claims associated with it. For example, consider a driving license. This is a single identity which contains a number of claims - FirstName, LastName, DateOfBirth, Address and which vehicles you are allowed to drive. Your passport would be a different identity with a different set of claims.




*Finally, once you are through security, you make your way to the VIP lounge, and are asked to prove your VIP status with the VIP Number claim. This could be in the form of a VIP card, which would be another form of identity and would verify the claim requested. If you did not have a card, you could not present the requested claim, you would be denied access, and so would be asked to leave and stop making a scene.*

![](https://andrewlock.net/content/images/2016/08/Untitled.png)