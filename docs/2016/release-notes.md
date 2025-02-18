# v4.0.52 Release Notes

We've hope everyone's had a great X-mas holidays and are super-charged for a productive 2016!

To kick things off we're making your ServiceStack Services even more attractive to mobile and Java developers 
with first-class support for JetBrains modern and highly-productive [Kotlin](https://kotlinlang.org/) 
programming language including integration into Android Studio and enhanced Android JsonServiceClient support.

## [Kotlin](https://kotlinlang.org/) - a better language for Android and the JVM

![](https://raw.githubusercontent.com/ServiceStack/Assets/master/img/wikis/android-studio-splash-kotlin.png)

Whilst Java is the flagship language for the JVM, it's slow evolution, lack of modern features and distasteful
language additions have grown it into an cumbersome language to develop with, as illustrated in the 
[C# 101 LINQ Examples in Java](https://github.com/mythz/java-linq-examples) where it's by far the worst of all 
modern languages compared, making it a poor choice for a functional-style of programming that's especially painful
for Android development which is stuck on Java 7.

### [101 LINQ Examples in Kotlin](https://github.com/mythz/kotlin-linq-examples) vs [Java](https://github.com/mythz/java-linq-examples)

By contrast Kotlin is one of the 
[best modern languages for functional programming](https://github.com/mythz/kotlin-linq-examples) that's 
vastly more expressive, readable, maintainable and safer than Java. As Kotlin is being developed by JetBrains 
it also has great tooling support in **Android Studio**, **IntelliJ** and **Eclipse** and seamlessly integrates 
with existing Java code where projects can **mix-and-match Java and Kotlin** code together within the same application - 
making Kotlin a very attractive and easy choice for Android Development.

## [Kotlin Native Types!](https://github.com/ServiceStack/ServiceStack/wiki/Kotlin-Add-ServiceStack-Reference)

As we expect more Android and Java projects to be written in Kotlin in future we've added first-class 
[Add ServiceStack Reference](https://github.com/ServiceStack/ServiceStack/wiki/Add-ServiceStack-Reference) 
support for Kotlin with IDE integration in 
[Android Studio](http://developer.android.com/tools/studio/index.html) and 
[IntelliJ IDEA](https://www.jetbrains.com/idea/) where App Devlopers can create and update an end-to-end typed 
API with just a Menu Item click - enabling a highly-productive workflow for consuming ServiceStack Services!

No new IDE plugins were needed to enable Kotlin support which was added to the existing 
[ServiceStack IDEA plugin](https://github.com/ServiceStack/ServiceStack/wiki/Java-Add-ServiceStack-Reference#servicestack-idea-android-studio-plugin) 
that can Install or Updated to enable Kotlin ServiceStack Reference support in Android Studio or IntelliJ IDEA.

### Installing Kotlin

Kotlin support is enabled in Android Studio by installing the JetBrain's Kotlin plugin in project settings:

![](https://raw.githubusercontent.com/ServiceStack/Assets/master/img/wikis/kotlin/install-kotlin-plugins.png)

After it's installed, subsequent Restarts of Android Studio will now load with the **Kotlin** plugin enabled.

#### Configure Project to use Kotlin

After Kotlin is enabled in Android Studio you can configure which projects you want to have Kotlin support
by going to `Tools -> Kotlin -> Configure Kotlin in Project` on the File Menu:

![](https://raw.githubusercontent.com/ServiceStack/Assets/master/img/wikis/kotlin/kotlin-configure-project.png)

Configuring a project to support Kotlin just modifies that projects 
[build.gradle](https://github.com/mythz/kotlin-linq-examples/blob/master/src/app/build.gradle), applying the
necessary Android Kotlin plugin and build scripts needed to compile Kotlin files with your project. Once Kotlin
is configured with your project you'll get first-class IDE support for Kotlin `.kt` source files including 
intell-sense, integrated compiler analysis and feedback, refactoring and debugging support, etc.

One convenient feature that's invaluable for porting Java code and learning Kotlin is the 
[Converting Java to Kotlin](https://kotlinlang.org/docs/tutorials/kotlin-android.html#converting-java-code-to-kotlin)
Feature which can be triggered by selecting a `.java` class and clicking `Ctrl + Alt + Shift + K` keyboard short-cut
(or using [Find Action](https://kotlinlang.org/docs/tutorials/kotlin-android.html#converting-java-code-to-kotlin)).

### Kotlin Add ServiceStack Reference

To add a ServiceStack Reference, right-click (or press `Ctrl+Alt+Shift+R`) on the **Package folder** in your 
Java sources where you want to add the POJO DTO's. This will bring up the **New >** Items Context Menu where 
you can click on the **ServiceStack Reference...** Menu Item to open the **Add ServiceStack Reference** Dialog: 

![Add ServiceStack Reference Kotlin Context Menu](https://raw.githubusercontent.com/ServiceStack/Assets/master/img/wikis/kotlin/package-add-servicestack-reference.png)

The **Add ServiceStack Reference** Dialog will be partially populated with the selected **Package** with the 
package where the Dialog was launched from and the **File Name** defaulting to `dtos.kt` where the generated 
Kotlin DTO's will be added to. All that's missing is the url of the remote ServiceStack instance you wish to 
generate the DTO's for, e.g: `http://techstacks.io`:

![](https://raw.githubusercontent.com/ServiceStack/Assets/master/img/wikis/kotlin/kotlin-add-servicestack-reference.png)

Clicking **OK** will add the 
[dtos.kt](https://github.com/ServiceStackApps/TechStacksKotlinApp/blob/master/src/TechStacks/app/src/main/java/servicestack/net/techstackskotlin/dtos.kt)
file to your project and modifies the current Project's **build.gradle** 
file dependencies list with the new **net.servicestack:android** dependency containing the JSON 
ServiceClients which is used together with the remote Servers DTO's to enable its typed Web Services API. If
for some reason you wish to instead add Java DTO's to your project instead of Kotlin, just rename the `dtos.kt` 
file extension to `dtos.java` and it will import Java classes instead.

> As the Module's **build.gradle** file was modified you'll need to click on the **Sync Now** link in the top yellow banner to sync the **build.gradle** changes which will install or remove any modified dependencies.


### Update ServiceStack Reference

Like other Native Type languages, the generated DTO's can be further customized by modifying any of the options available in the header comments:

```
/* Options:
Date: 2015-04-17 15:16:08
Version: 1
BaseUrl: http://techstacks.io

Package: org.layoric.myapplication
GlobalNamespace: techstackdtos
//AddPropertyAccessors: True
//SettersReturnThis: True
//AddServiceStackTypes: True
//AddResponseStatus: False
//AddImplicitVersion: 
//IncludeTypes: 
//ExcludeTypes: 
//DefaultImports: java.math.*,java.util.*,net.servicestack.client.*,com.google.gson.annotations.*
*/
...
```

For example the package name can be changed by uncommenting the **Package:** option with the new package name, then either right-click on the file to bring up the file context menu or use Android Studio's **Alt+Enter** keyboard shortcut then click on **Update ServiceStack Reference** to update the DTO's with any modified options:

![](https://raw.githubusercontent.com/ServiceStack/Assets/master/img/wikis/kotlin/kotlin-update-servicestack-reference.png)


### JsonServiceClient Usage

Both Java and Kotlin use the same `JsonServiceClient` that you need to initialize with the **BaseUrl** of 
the remote ServiceStack instance you want to access, e.g:

```kotlin
val client = JsonServiceClient("http://techstacks.io")
```

> The JsonServiceClient is made available after the [net.servicestack:android](https://bintray.com/servicestack/maven/ServiceStack.Android/view) package is automatically added to your **build.gradle** when adding a ServiceStack reference.

Typical usage of the Service Client is the same in .NET where you just need to send a populated Request DTO 
and the Service Client will return a populated Response DTO, e.g:

```kotlin
val response:AppOverviewResponse? = client.get(AppOverview())
val allTiers:ArrayList<Option> = response.AllTiers
val topTech:ArrayList<TechnologyInfo> = response.TopTechnologies
```

As Kotlin has proper type inference, the explicit types are unnecceessary. Here's a typical example using a populated Request DTO:

```kotlin
var request = GetTechnology()
request.Slug = "servicestack"

val response = client.get(request)
```

### Custom Route Example

When preferred you can also consume Services using a custom route by supplying a string containing the route 
and/or Query String. As no type info is available you'll need to specify the Response DTO class to deserialize 
the response into, e.g:

```kotlin
val response = client.get("/overview", OverviewResponse::class.java)

//Using an Absolute Url:
val response = client.get("http://techstacks.io/overview", OverviewResponse::class.java)
```

### AutoQuery Example Usage

You can also send requests composed of both a Typed DTO and untyped String Map by providing a Hash Map of 
additional args. This is typically used when querying 
[implicit conventions in AutoQuery services](https://github.com/ServiceStack/ServiceStack/wiki/Auto-Query#implicit-conventions), e.g:

```kotlin
val response = client.get(FindTechnologies(), hashMapOf(Pair("DescriptionContains","framework")))
```

## AndroidServiceClient Async Usage

To make use of Async API's in an Android App (which you'll want to do to keep web service requests off the 
Main UI thread), you'll instead need to use an instance of `AndroidServiceClient` which as it inherits 
`JsonServiceClient` can be used to perform both Sync and Async requests which can be instantiated with:

```kotlin
val client = AndroidServiceClient("http://techstacks.io")
```
To provide an optimal experience for Kotlin and Java 8, we've added 
[SAM overloads](https://kotlinlang.org/docs/reference/java-interop.html#sam-conversions) 
using the new `AsyncSuccess<T>`, `AsyncSuccessVoid` and `AsyncError` interfaces which as they only contain 
a single method are treated like a lambda in Kotlin and Java 8 allowing you to make async requests with just:

```kotlin
client.getAsync(Overview(), AsyncSuccess<OverviewResponse> {
        var topUsers = it.TopUsers
    }, AsyncError {
        it.printStackTrace()
    })
```

Instead of the previously more verbose anonymous AsyncResult interface used in Java 7:

```kotlin
client.getAsync(Overview(), object: AsyncResult<OverviewResponse>() {
    override fun success(response: OverviewResponse?) {
        var topUsers = response!!.TopUsers
    }
    override fun error(ex: Exception?) {
        ex?.printStackTrace()
    }
})
```

### Custom Service Examples

Just like the `JsonServiceClient` Sync examples above there a number of flexible options for executing 
Custom Async Requests, e.g: 

```kotlin
//Relative Url:
client.getAsync("/overview", OverviewResponse::class.java,
    AsyncSuccess<OverviewResponse?> {  
    })

//Absolute Url:
client.getAsync("http://techstacks.io/overview", OverviewResponse::class.java,
    AsyncSuccess<OverviewResponse>() {
    })

//AutoQuery Example:
client.getAsync(FindTechnologies(), hashMapOf(Pair("DescriptionContains", "framework")),
    AsyncSuccess<QueryResponse<Technology>>() {
    })
```

#### Download Raw Image Async Example

Example downloading raw Image bytes and loading it into an Android Image `Bitmap`:

```kotlin
client.getAsync("https://servicestack.net/img/logo.png", {
    val img = BitmapFactory.decodeByteArray(it, 0, it.size);
})
```

#### Send Raw String or byte[] Requests

You can easily get the raw string Response from Request DTO's that return are annotated with `IReturn<string>`, e.g:
 
```java
open class HelloString : IReturn<String> { ... }

var request = HelloString()
request.name = "World"

val response:String? = client.get(request)
```

You can also specify that you want the raw UTF-8 `byte[]` or `String` response instead of a the deserialized 
Response DTO by specifying the Response class you want returned, e.g:

```kotlin
val response:ByteArray = client.get("/hello?Name=World", ByteArray::class.java);
```

### Typed Error Handling

Thanks to Kotlin also using typed Exceptions for error control flow, error handling in Kotlin will be instantly 
familiar to C# devs which also throws a typed `WebServiceException` containing the remote servers structured 
error data:

```kotlin
var request = ThrowType()
request.Type = "NotFound"
request.message = "not here"

try {
    val response = client.post(request)
} catch(webEx: WebServiceException) {
    val status = webEx.responseStatus
    status.message    //= not here
    status.stackTrace //= (Server StackTrace)
}
```

### Async Error Handling

Whilst Async Error handers can cast into a `WebServiceException` to access the structured error response:

```kotlin
client.postAsync(ThrowError(), AsyncSuccess<ThrowErrorResponse> { },
    AsyncError {
        val webEx = it as WebServiceException

        val status = webEx.responseStatus
        status.message    //= not here
        status.stackTrace //= (Server StackTrace)
    })
```

### JsonServiceClient Error Handlers

To make it easier to generically handle Web Service Exceptions, the Java Service Clients also support static Global Exception handlers by assigning `AndroidServiceClient.GlobalExceptionFilter`, e.g:
```kotlin
AndroidServiceClient.GlobalExceptionFilter = ExceptionFilter { res:HttpURLConnection?, ex ->
}
```

As well as local Exception Filters by specifying a handler for `client.ExceptionFilter`, e.g:
```kotlin
client.ExceptionFilter = ExceptionFilter { res:HttpURLConnection?, ex ->
}
```

See the [Kotlin Add ServiceStack Reference](https://github.com/ServiceStack/ServiceStack/wiki/Kotlin-Add-ServiceStack-Reference) 
wiki for more docs on consuming ServiceStack Services from Kotlin.

## Example [TechStacks Android App](https://github.com/ServiceStackApps/TechStacksKotlinApp)

To demonstrate Kotlin Native Types in action we've ported the Java 
[TechStacks Android App](https://github.com/ServiceStackApps/TechStacksAndroidApp) to a native 
Android App written in Kotlin to showcase the responsiveness and easy-of-use of leveraging 
Kotlin Add ServiceStack Reference in Android Projects. 

[![](https://raw.githubusercontent.com/ServiceStack/Assets/master/img/release-notes/techstacks-kotlin-app.png)](https://github.com/ServiceStackApps/TechStacksAndroidApp)

Checkout the [TechStacks Kotlin Android App](https://github.com/ServiceStackApps/TechStacksKotlinApp) 
repository for a nice overview of how it leverages Kotlin Native Types and iOS-inspired Data Binding to easily 
develop services-heavy Mobile Apps.

### Kotlin Android Resources

To help getting started, here are some useful resources helping to develop Android Apps with Kotlin:

 - [Getting started with Android and Kotlin](https://kotlinlang.org/docs/tutorials/kotlin-android.html) <small>_(kotlinlang.org)_</small>
 - [Kotlin for Android Developers](http://www.javaadvent.com/2015/12/kotlin-android.html) <small>_(javaadvent.com)_</small>
 - [Android Development with Kotlin - Jake Wharton](https://www.youtube.com/watch?v=A2LukgT2mKc&feature=youtu.be) <small>_(youtube.com)_</small>


## Improved [Java and Android ServiceClient](https://github.com/ServiceStack/ServiceStack.Java)

### Fewer dependencies

We've continued making improvements to Java and Android Service Clients which now have fewer dependencies
initially triggered by [Google removing Apache HTTP Client](http://developer.android.com/about/versions/marshmallow/android-6.0-changes.html#behavior-apache-http-client)
in Android 6.0. Previously the `AndroidServiceClient` **net.servicestack:android** package contained dependencies
on the pure Java **net.servicestack:client** package as well as the external Apache Client. Both depdencies
have been removed, the **android** package now uses the HTTP classes built into Android and all **client** classes
have been merged into the **android** package. 

The **net.servicestack:client** package continues to be available for pure Java clients and remains 
source-compatible with the `JsonServiceClient` classes in the **android** package.

### Integrated Basic Auth

We've added HTTP Basic Auth support to `JsonServiceClient` following the implementation in .NET Service Client
where you can specify the users credentials and whether you always want to send Basic Auth with each request by:

```java
client.setCredentials(userName, password);
client.setAlwaysSendBasicAuthHeaders(true);

TestAuthResponse response = client.get(new TestAuth());
```

It also supports processing challenged 401 Auth HTTP responses where it will transparently replay the failed 
request with the Basic Auth Headers:

```java
client.setCredentials(userName, password);

TestAuthResponse response = client.get(new TestAuth());
```

Although this has the additional latency of waiting for a failed 401 response before sending an authenticated request.

### Cookies-enabled Service Client

The `JsonServiceClient` now initializes a `CookieManager` in its constructor to enable any Cookies recevied to
be added on subsequent requests to allow you to make authenticated requests after authenticating, e.g:

```java
AuthenticateResponse authResponse = client.post(new Authenticate()
    .setProvider("credentials")
    .setUserName(userName)
    .setPassword(password));

TestAuthResponse response = client.get(new TestAuth());
``` 

## [OrmLite](https://github.com/ServiceStack/ServiceStack.OrmLite)

### Async PostgreSQL Support

The [Npgsql](http://www.npgsql.org) ADO.NET PostgreSQL provider [underwent a major upgrade in v3](http://www.npgsql.org/npgsql-3.0-released/)
where [existing 2.x versions](http://www.npgsql.org/2.2.6-release/) are now considered obsolete. As a 
result we've upgraded 
[ServiceStack.OrmLite.PostgreSQL](https://www.nuget.org/packages/ServiceStack.OrmLite.PostgreSQL/)
to use the latest **v3.0.5** of Npgsql which is only avaliable for .NET 4.5+ projects. We're also distributing
.NET 4.0 builds of OrmLite in the same NuGet package but you'll need to use manually reference the **2.x** Npgsql 
dependency which contains .NET 4.0 .dll. 

The primary benefit of upgrading means PostgreSQL now has true Async support where you can now use all of
[OrmLite's Async APIs](https://github.com/ServiceStack/ServiceStack.OrmLite#async-api-overview) with PostgreSQL!
See [ApiPostgreSqlTestsAsync.cs](https://github.com/ServiceStack/ServiceStack.OrmLite/blob/master/tests/ServiceStack.OrmLiteV45.Tests/ApiPostgreSqlTestsAsync.cs)
for a number of Async API's in action.

### Parameterized SQL Expressions

When typed SQL Expressions were first added they constructed SQL inline. We've been slow to migrate to using 
parameterized queries which was first enabled for Oracle behind a 
`OrmLiteConfig.UseParameterizeSqlExpressions = true;` flag. We've since carefully maintained separate code-paths
to ensure any migration efforts wouldn't affect existing queries. In the last release we extended support to 
SQL Server under the same flag. 

In this release we've enabled it for every RDBMS provider and have made parameterized queries the default. 

So now typed SQL Expressions will use parameterized queries by default, e.g:

```csharp
db.Select<Person>(x => x.Age > 40);
db.GetLastSql(); //= SELECT "Id", "FirstName", "LastName", "Age" FROM "Person" WHERE ("Age" > @0)
```

For now all supported RDBMS's can still opt-in to revert to in-line SQL with:

```csharp
OrmLiteConfig.UseParameterizeSqlExpressions = false;

db.Select<Person>(x => x.Age > 40);
db.GetLastSql(); //= SELECT "Id", "FirstName", "LastName", "Age" FROM "Person" WHERE ("Age" > 40)
```

However we've deprecated `OrmLiteConfig.UseParameterizeSqlExpressions` as we want to remove the legacy code-paths 
as soon as possible. Our entire test suite passes under either option so we expect this change to be a transparent 
implementation detail not affecting existing behavior. However if you do find any issues with this change please 
[submit them to us](https://github.com/ServiceStack/Issues) as we plan to remove the legacy implementation 
if there aren't any reported issues. In the meantime you can use the above flag to revert to the existing behavior.

More examples showing the difference between in-line and parameterized SQL Expressions can be seen in:

 - [ApiSqlServerTests.cs](https://github.com/ServiceStack/ServiceStack.OrmLite/blob/777084da84dadf972b63b0caef02b7801f63935b/tests/ServiceStack.OrmLite.Tests/ApiSqlServerTests.cs)
 - [ApiSqlServerTests.NonParam.cs](https://github.com/ServiceStack/ServiceStack.OrmLite/blob/777084da84dadf972b63b0caef02b7801f63935b/tests/ServiceStack.OrmLite.Tests/ApiSqlServerTests.NonParam.cs)

### Parameterized Updates

In the migration to Parameterized queries we've also migrated the Update API's, e.g:

```csharp
db.Update(new Person { Id = 1, FirstName = "Jimi", LastName = "Hendrix" });
db.GetLastSql() //= UPDATE "Person" SET "FirstName"=@FirstName, "LastName"=@LastName WHERE "Id"=@Id
```

### Parameterized ExecuteSql

The new `ExecuteSql()` API makes it easy to execute Custom SQL with parameterized values using an anon object:

```csharp
Db.ExecuteSql("UPDATE page_stats SET fav_count = @favCount WHERE ref_id = @refId and ref_type = 'tech'",
              new { refId = techFav.Key, favCount = techFav.Value });
```

Whilst the Async alternative is useful for non-blocking fire-and-forget RDBMS updates, e.g. TechStacks uses this for 
[updating page view counts](https://github.com/ServiceStackApps/TechStacks/blob/06acc775a65b74610b43878aea4543cbd7a9912c/src/TechStacks/TechStacks.ServiceInterface/TechExtensions.cs#L53):
    
```csharp
Db.ExecuteSqlAsync("UPDATE page_stats SET view_count = view_count + 1 WHERE id = @id", new { id })
```

### LoadSelect Typed Include References

Similar to `LoadSingleById`, there's now a typed API that lets you selectively load refernces in `LoadSelect` queries, e.g:

```csharp
var customers = db.LoadSelect<Customer>(x => x.Name.StartsWith("A"), 
    include: x => new { x.PrimaryAddress });
```

## Updated [Stripe Gateway](https://github.com/ServiceStack/Stripe)

StripeGateway has been updated to use the latest 2015-10-13 API version thanks to [@jklemmack](https://github.com/jklemmack).
Please refer to [Stripe's API Chengelog](https://stripe.com/docs/upgrades#api-changelog) for the complete list of
API changes. Most of the API Collections now supports paging with the `Limit`, `StartingAfter` and `EndingBefore`
properties added on the Request DTO's.

There were a few source-incompatible breaking changes where `Cards` have been renamed to `Sources`, `Last4` was
renamed to `DynamicLast4` and the collection `Count` is renamed to `TotalCount` so to access the total size of
a collection, instead of:

```csharp
response.Cards.Count
```

You'd now use:

```csharp
response.Sources.TotalCount
```

### Customize urls used with `IUrlFilter`

Request DTO's can customize urls used in Service Clients or any libraries using ServiceStack's typed 
[Reverse Routing](https://github.com/ServiceStack/ServiceStack/wiki/Routing#reverse-routing) by having 
Request DTO's implement 
[IUrlFilter](https://github.com/ServiceStack/ServiceStack/blob/master/src/ServiceStack.Interfaces/IUrlFilter.cs).

ServiceStack's [Stripe Gateway](https://github.com/ServiceStack/Stripe) takes advantage of ServiceStack's
typed Routing feature to implement its 
[Open-Ended, Declarative Message-based APIs](https://github.com/ServiceStack/Stripe#open-ended-declarative-message-based-apis)
with minimal effort.

In order to match Stripe's unconventional syntax for specifying arrays on the QueryString of their 3rd party
REST API we use `IUrlFilter` to customize the url that's used. E.g. we need to specify `include[]` in order
for the Stripe API to return any optional fields like **total_count**.

```csharp
[Route("/customers")]
public class GetStripeCustomers : IGet, IReturn<StripeCollection<StripeCustomer>>, IUrlFilter
{
    public GetStripeCustomers() 
    {
        Include = new[] { "total_count" };
    }

    [IgnoreDataMember]
    public string[] Include { get; set; }

    public string ToUrl(string absoluteUrl)
    {
        return Include == null ? absoluteUrl 
            : absoluteUrl.AddQueryParam("include[]", string.Join(",", Include));
    }
}
```

> `[IgnoreDataMember]` is used to hide the property being emitted using the default convention

Which when sending the Request DTO:

```csharp
var response = client.Get(new GetStripeCustomers());
```

Generates and sends the relative url:

    /customers?include[]=total_count

Which has the effect of populating the `TotalCount` property in the typed `StripeCollection<StripeCustomer>` response.

## Web Framework

### Structured Request Binding Errors

Previously type conversion errors would throw a generic `RequestBindingException` to indicate the Request was
malformed. They are now being converted into a structured error so the same error handling logic used to handle
[field validation errors](https://github.com/ServiceStack/ServiceStack/wiki/Validation) can also handle request
binding exceptions, e.g:

try
{
    var response = client.Get<ErrorRequestBinding>("/errorrequestbinding?Int=string");
}
catch (WebServiceException ex)
{
    ex.ResponseStatus.Message //= Unable to bind to request 'ErrorRequestBinding': Input string was not in a correct format.

    var fieldError = ex.GetFieldErrors()[0];
    fieldError.FieldName //= Int
    fieldError.ErrorCode //= SerializationException
    fieldError.Message   //= 'string' is an Invalid value for 'Int'
}
 
Special thanks to [@georgehemmings](https://github.com/georgehemmings) for his contributions to this feature. 
 
### Scalable [Server Events](https://github.com/ServiceStack/ServiceStack/wiki/Server-Events)

[@Nness](https://github.com/Nness) upgraded our existing Server Events implementation based on manual array 
re-sizing and custom locks to use `ConcurrentDictionary` to 
[solve their scalability issues](https://github.com/ServiceStack/ServiceStack/pull/1014)
they were having at 25-30k concurrent Server Event connections.

The default synchronous `WriteEvent` implementation can be overridden which .NET 4.5 applications can take 
advantage to use asynchronous Write and Flush API's with:

```csharp
Plugins.Add(new ServerEventsFeature
{
    WriteEvent = (res, frame) =>
    {
        var aspRes = (HttpResponseBase)res.OriginalResponse;
        var bytes = frame.ToUtf8Bytes();
        aspRes.OutputStream.WriteAsync(bytes, 0, bytes.Length)
            .Then(_ => aspRes.OutputStream.FlushAsync());
    }
});
```

## [Metadata pages](https://github.com/ServiceStack/ServiceStack/wiki/Metadata-page)

To avoid repitive noise in each Metadata Operation Page the common `ResposneStatus` DTO's were omitted, if
you prefer they can now be enabled with:

```csharp
this.GetPlugin<MetadataFeature>().ShowResponseStatusInMetadataPages = true;
```

## [AutoQuery](https://github.com/ServiceStack/ServiceStack/wiki/Auto-Query)

### Querying NULL

You can implicitly query a Column is null by specifying a property with no value, e.g:

    /rockstars?DateDied=
    
Will return all Rockstars where **DateDied IS NULL**.

## Other Changes

 - `ISequenceSource` changed to use longs
 - Add Support for Fluent Validation's `RuleForEach()`
 - Use `AuthFeature.HtmlLogoutRedirect` to specify the browser redirect after logout
 - Change Exception returned by overriding `ResolveResponseException()` in AppHost

---


## [2015 Release Notes](https://github.com/ServiceStack/ServiceStack/blob/master/docs/2015/release-notes.md)
