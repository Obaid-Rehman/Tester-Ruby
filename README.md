# Getting Started with APIMATIC Calculator

## Getting Started

### Introduction

Simple calculator API hosted on APIMATIC

### Building

The generated code depends on a few Ruby gems. The references to these gems are added in the gemspec file. The easiest way to resolve the dependencies, build the gem and install it is through Rake:

1. Install Rake if not already installed: `gem install rake`
2. Install Bundler if not already installed: `gem install bundler`
3. From terminal/cmd navigate to the root directory of the SDK.
4. Invoke: `rake install`

Alternatively, you can build and install the gem manually:

1. From terminal/cmd navigate to the root directory of the SDK.
2. Run the build command: `gem build apimatic_calculator.gemspec`
3. Run the install command: `gem install apimatic_calculator-2.0.0.gem`

![Installing Gem](https://apidocs.io/illustration/ruby?workspaceFolder=ApimaticCalculator&gemVer=2.0.0&gemName=apimatic_calculator&step=buildSDK)

### Installation

The following section explains how to use the apimatic_calculator ruby gem in a new Rails project using RubyMine&trade;. The basic workflow presented here is also applicable if you prefer using a different editor or IDE.

#### 1. Starting a new project

Close any existing projects in RubyMine&trade; by selecting `File -> Close Project`. Next, click on `Create New Project` to create a new project from scratch.

![Create a new project in RubyMine - Step 1](https://apidocs.io/illustration/ruby?workspaceFolder=ApimaticCalculator&step=createNewProject0)

Next, provide `TestApp` as the project name, choose `Rails Application` as the project type, and click `OK`.

![Create a new Rails Application in RubyMine - Step 2](https://apidocs.io/illustration/ruby?workspaceFolder=ApimaticCalculator&step=createNewProject1)

In the next dialog make sure that the correct Ruby SDK is being used (minimum 2.0.0) and click `OK`.

![Create a new Rails Application in RubyMine - Step 3](https://apidocs.io/illustration/ruby?workspaceFolder=ApimaticCalculator&step=createNewProject2)

#### 2. Add reference of the gem

In order to use the Tester gem in the new project we must add a gem reference. Locate the `Gemfile` in the Project Explorer window under the `TestApp` project node. The file contains references to all gems being used in the project. Here, add the reference to the library gem by adding the following line: `gem 'apimatic_calculator', '2.0.0'`

![Add new reference to the Gemfile](https://apidocs.io/illustration/ruby?workspaceFolder=ApimaticCalculator&gemVer=2.0.0&gemName=apimatic_calculator&step=addReference)

#### 3. Adding a new Rails Controller

Once the `TestApp` project is created, a folder named `controllers` will be visible in the *Project Explorer* under the following path: `TestApp > app > controllers`. Right click on this folder and select `New -> Run Rails Generator...`.

![Run Rails Generator on Controllers Folder](https://apidocs.io/illustration/ruby?workspaceFolder=ApimaticCalculator&gemVer=2.0.0&gemName=apimatic_calculator&step=addCode0)

Selecting the said option will popup a small window where the generator names are displayed. Here, select the `controller` template.

![Create a new Controller](https://apidocs.io/illustration/ruby?workspaceFolder=ApimaticCalculator&step=addCode1)

Next, a popup window will ask you for a Controller name and included Actions. For controller name provide `Hello` and include an action named `Index` and click `OK`.

![Add a new Controller](https://apidocs.io/illustration/ruby?workspaceFolder=ApimaticCalculator&gemVer=2.0.0&gemName=apimatic_calculator&step=addCode2)

A new controller class named `HelloController` will be created in a file named `hello_controller.rb` containing a method named `Index`. In this method, add code for initialization and a sample for its usage.

![Initialize the library](https://apidocs.io/illustration/ruby?workspaceFolder=ApimaticCalculator&gemName=apimatic_calculator&step=addCode3)

### Initialize the API Client

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| `environment` | Environment | The API environment. <br> **Default: `Environment.PRODUCTION`** |
| `timeout` | `Float` | The value to use for connection timeout. <br> **Default: 60** |
| `max_retries` | `Integer` | The number of times to retry an endpoint call if it fails. <br> **Default: 0** |
| `retry_interval` | `Float` | Pause in seconds between retries. <br> **Default: 1** |
| `backoff_factor` | `Float` | The amount to multiply each successive retry's interval amount by in order to provide backoff. <br> **Default: 2** |
| `retry_statuses` | `Array` | A list of HTTP statuses to retry. <br> **Default: [408, 413, 429, 500, 502, 503, 504, 521, 522, 524]** |
| `retry_methods` | `Array` | A list of HTTP methods to retry. <br> **Default: %i[get put]** |

The API client can be initialized as follows:

```ruby
client = ApimaticCalculator::Client.new(
  environment: Environment::PRODUCTION,
)
```

### Test the SDK

To run the tests, navigate to the root directory of the SDK in your terminal and execute the following command:

```
rake
```

## Client Class Documentation

### APIMATIC Calculator Client

The gateway for the SDK. This class acts as a factory for the Controllers and also holds the configuration of the SDK.

### Controllers

| Name | Description |
|  --- | --- |
| simple_calculator | Gets SimpleCalculatorController |

## API Reference

### List of APIs

* [Simple Calculator](#simple-calculator)

### Simple Calculator

#### Overview

##### Get instance

An instance of the `SimpleCalculatorController` class can be accessed from the API Client.

```
simple_calculator_controller = client.simple_calculator
```

#### Get Calculate

Calculates the expression using the specified operation.

:information_source: **Note** This endpoint does not require authentication.

```ruby
def get_calculate(options = {})
```

##### Parameters

| Parameter | Type | Tags | Description |
|  --- | --- | --- | --- |
| `operation` | [`OperationTypeEnum`](#operation-type) | Template, Required | The operator to apply on the variables |
| `x` | `Float` | Query, Required | The LHS value |
| `y` | `Float` | Query, Required | The RHS value |

##### Response Type

`Float`

##### Example Usage

```ruby
collect = {}

operation = OperationTypeEnum::MULTIPLY
collect['operation'] = operation;

x = 222.14
collect['x'] = x;

y = 165.14
collect['y'] = y;

result = simple_calculator_controller.get_calculate(collect)
```

## Model Reference

### Enumerations

* [Operation Type](#operation-type)

#### Operation Type

Possible operators are sum, subtract, multiply, divide

##### Class Name

`OperationTypeEnum`

##### Fields

| Name | Description |
|  --- | --- |
| `SUM` | Represents the sum operator |
| `SUBTRACT` | Represents the subtract operator |
| `MULTIPLY` | Represents the multiply operator |
| `DIVIDE` | Represents the divide operator |

## Utility Classes Documentation

### ApiHelper Class

API utility class.

### Methods

| Name | Return Type | Description |
|  --- | --- | --- |
| json_deserialize | Hash | Deserializes a JSON string to a Ruby Hash. |
| rfc3339 | DateTime | Safely converts a string into an RFC3339 DateTime object. |

## Common Code Documentation

### HttpResponse

Http response received.

#### Properties

| Name | Type | Description |
|  --- | --- | --- |
| status_code | Integer | The status code returned by the server. |
| reason_phrase | String | The reason phrase returned by the server. |
| headers | Hash | Response headers. |
| raw_body | String | Response body. |
| request | HttpRequest | The request that resulted in this response. |

### HttpRequest

Represents a single Http Request.

#### Properties

| Name | Type | Tag | Description |
|  --- | --- | --- | --- |
| http_method | HttpMethodEnum |  | The HTTP method of the request. |
| query_url | String |  | The endpoint URL for the API request. |
| headers | Hash | Optional | Request headers. |
| parameters | Hash | Optional | Request body. |

