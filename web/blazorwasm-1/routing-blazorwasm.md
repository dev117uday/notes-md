# Routing Blazorwasm

## Routing the BlazorWASM

### add route to page

```text
@page "/BlazorRoute"
@page "/DifferentBlazorRoute"

<h1>Blazor routing</h1>
```

### add route not found message in `app.razor` file

```markup
<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <h1>Sorry</h1>
        <p>Sorry, there's nothing at this address.</p> b
    </NotFound>
</Router>
```

### route parameters

```csharp
@page "/RouteParameter/{text}"
@page "/RouteParameterOptional/{text?}"

<h1>Blazor is @Text!</h1>

@code {
    [Parameter]
    public string Text { get; set; }

    protected override void OnParametersSet()
    {
        Text = Text ?? "fantastic";
    }
}
```

### route constraints

```csharp
@page "/user/{Id:int}"

<h1>User Id: @Id</h1>

@code {
    [Parameter]
    public int Id { get; set; }
}
```

![](../../.gitbook/assets/image%20%287%29.png)

### multiple parameters in route

```csharp
@page "/user/{Id:int}/{Option:bool?}"
```

### Routing with URLs that contain dots

```csharp
@page "/example/{param?}"

<p>
    Param: @Param
</p>

@code {
    [Parameter]
    public string Param { get; set; }
}
```

In `Startup.cs`

```csharp
endpoints.MapFallbackToFile("/example/{param?}", "index.html");
endpoints.MapFallbackToPage("/example/{param?}", "/_Host");
```

### catch all routes

```csharp
@page "/catch-all/{*pageRoute}"

@code {
    [Parameter]
    public string PageRoute { get; set; }
}
```

## Configuration in BlazorWASM

* `Program.cs`

```csharp
using Microsoft.Extensions.Configuration;

var http = new HttpClient()
{
    BaseAddress = new Uri(builder.HostEnvironment.BaseAddress)
};

builder.Services.AddScoped(sp => http);

using var response = await http.GetAsync("cars.json");
using var stream = await response.Content.ReadAsStreamAsync();

builder.Configuration.AddJsonStream(stream);
```

* create a file inside `wwwroot/cars.json`

```javascript
{
    "size": "tiny"
}
```

### Adding dependency in the app

* supported lifetimes 
  * Transient
  * Singleton
  * Scoped : `blazorwasm` doesn't support scoped as of writing this doc
* in `Startup.cs` 

```csharp
builder.Services.AddSingleton<IMyDependency, MyDependency>();
```

```csharp
@inject IDataAccess DataRepository
DataRepository.SomeMethod();
```

or in `.cs`

```csharp
using Microsoft.AspNetCore.Components;

public class ComponentBase : IComponent
{
    [Inject]
    protected IDataAccess DataRepository { get; set; }

    ...
}


// in the page
@page "/demo"
@inherits ComponentBase

<h1>Demo Component</h1>
```

### DI in services

```csharp
using System.Net.Http;

public class DataAccess : IDataAccess
{
    public DataAccess(HttpClient http)
    {
        ...
    }
}
```

