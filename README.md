# Clean Architecture Solution Template

[![Build](https://github.com/jasontaylordev/CleanArchitecture/actions/workflows/build.yml/badge.svg)](https://github.com/jasontaylordev/CleanArchitecture/actions/workflows/build.yml)
[![CodeQL](https://github.com/jasontaylordev/CleanArchitecture/actions/workflows/codeql.yml/badge.svg)](https://github.com/jasontaylordev/CleanArchitecture/actions/workflows/codeql.yml)
[![Nuget](https://img.shields.io/nuget/v/Clean.Architecture.Solution.Template?label=NuGet)](https://www.nuget.org/packages/Clean.Architecture.Solution.Template)
[![Nuget](https://img.shields.io/nuget/dt/Clean.Architecture.Solution.Template?label=Downloads)](https://www.nuget.org/packages/Clean.Architecture.Solution.Template)
![Twitter Follow](https://img.shields.io/twitter/follow/jasontaylordev?label=Follow&style=social)

The goal of this template is to provide a straightforward and efficient approach to enterprise application development, leveraging the power of Clean Architecture and ASP.NET Core. Using this template, you can effortlessly create a Single Page App (SPA) with ASP.NET Core and Angular or React, while adhering to the principles of Clean Architecture. Getting started is easy - simply install the **.NET template** (see below for full details).

If you find this project useful, please give it a star. Thanks! ⭐

## Getting Started

The following prerequisites are required to build and run the solution:

- [.NET 9.0 SDK](https://dotnet.microsoft.com/download/dotnet/9.0) (latest version)
- [Node.js](https://nodejs.org/) (latest LTS, only required if you are using Angular or React)

The easiest way to get started is to install the [.NET template](https://www.nuget.org/packages/Clean.Architecture.Solution.Template):
```
dotnet new install Clean.Architecture.Solution.Template
```

Once installed, create a new solution using the template. You can choose to use Angular, React, or create a Web API-only solution. Specify the client framework using the `-cf` or `--client-framework` option, and provide the output directory where your project will be created. Here are some examples:

To create a Single-Page Application (SPA) with Angular and ASP.NET Core:
```bash
dotnet new ca-sln --client-framework Angular --output YourProjectName
```

To create a SPA with React and ASP.NET Core:
```bash
dotnet new ca-sln -cf React -o YourProjectName
```

To create a ASP.NET Core Web API-only solution:
```bash
dotnet new ca-sln -cf None -o YourProjectName
```

Launch the app:
```bash
cd src/Web
dotnet run
```

To learn more, run the following command:
```bash
dotnet new ca-sln --help
```

You can create use cases (commands or queries) by navigating to `./src/Application` and running `dotnet new ca-usecase`. Here are some examples:

To create a new command:
```bash
dotnet new ca-usecase --name CreateTodoList --feature-name TodoLists --usecase-type command --return-type int
```

To create a query:
```bash
dotnet new ca-usecase -n GetTodos -fn TodoLists -ut query -rt TodosVm
```

To learn more, run the following command:
```bash
dotnet new ca-usecase --help
```

## Database

The template supports [PostgresSQL](https://www.postgresql.org), [SQLite](https://www.sqlite.org/), and [SQL Server](https://learn.microsoft.com/en-us/sql/sql-server/what-is-sql-server) (default option). Specify the database to use with the `--database` option:

```bash
dotnet new ca-sln --database [postgresql|sqlite|sqlserver]
```

When you run the application, the database will be automatically created (if necessary) and the latest migrations will be applied.

Running database migrations is easy. Ensure you add the following flags to your command (values assume you are executing from repository root)

* `--project src/Infrastructure` (optional if in this folder)
* `--startup-project src/Web`
* `--output-dir Data/Migrations`

For example, to add a new migration from the root folder:

 `dotnet ef migrations add "SampleMigration" --project src\Infrastructure --startup-project src\Web --output-dir Data\Migrations`

## Deploy

This template is structured to follow the Azure Developer CLI (azd). You can learn more about `azd` in the [official documentation](https://learn.microsoft.com/en-us/azure/developer/azure-developer-cli). To get started:

```bash
# Log in to Azure
azd auth login

# Provision and deploy to Azure
azd up
```

## Technologies

* [ASP.NET Core 9](https://docs.microsoft.com/en-us/aspnet/core/introduction-to-aspnet-core)
* [Entity Framework Core 9](https://docs.microsoft.com/en-us/ef/core/)
* [Angular 18](https://angular.dev/) or [React 18](https://react.dev/)
* [MediatR](https://github.com/jbogard/MediatR)
* [AutoMapper](https://automapper.org/)
* [FluentValidation](https://fluentvalidation.net/)
* [NUnit](https://nunit.org/), [FluentAssertions](https://fluentassertions.com/), [Moq](https://github.com/devlooped/moq) & [Respawn](https://github.com/jbogard/Respawn)

## Versions
The main branch is now on .NET 9.0. The following previous versions are available:

* [8.0](https://github.com/jasontaylordev/CleanArchitecture/tree/net8.0)
* [7.0](https://github.com/jasontaylordev/CleanArchitecture/tree/net7.0)
* [6.0](https://github.com/jasontaylordev/CleanArchitecture/tree/net6.0)
* [5.0](https://github.com/jasontaylordev/CleanArchitecture/tree/net5.0)
* [3.1](https://github.com/jasontaylordev/CleanArchitecture/tree/netcore3.1)

## Learn More

* [Clean Architecture with ASP.NET Core 3.0 (GOTO 2019)](https://youtu.be/dK4Yb6-LxAk)
* [Clean Architecture with .NET Core: Getting Started](https://jasontaylor.dev/clean-architecture-getting-started/)

## Support

If you are having problems, please let me know by [raising a new issue](https://github.com/jasontaylordev/CleanArchitecture/issues/new/choose).

## License

This project is licensed with the [MIT license](LICENSE).


Dưới đây là giải thích chi tiết về **Clean Architecture Solution Template** mà bạn vừa trích dẫn:

---

## 🏛 Clean Architecture Solution Template là gì?

Đây là một **mẫu dự án (project template)** cho **.NET** được xây dựng dựa trên nguyên tắc **Clean Architecture**. Nó giúp bạn tạo nhanh một kiến trúc chuẩn cho ứng dụng doanh nghiệp, sử dụng **ASP.NET Core** kèm theo SPA (Single Page Application) với **Angular** hoặc **React**, mà vẫn tuân thủ các nguyên tắc tách biệt lớp (separation of concerns) và dễ mở rộng, bảo trì.

Mục tiêu chính của template:

- 🚀 **Bắt đầu nhanh**: Chỉ với một lệnh `dotnet new`, bạn đã có một kiến trúc chuẩn, sẵn sàng cho dự án.
- 🧩 **Kiến trúc sạch sẽ**: Giúp code dễ bảo trì, dễ test, dễ mở rộng.
- 🌐 **Hỗ trợ nhiều công nghệ phổ biến**: Angular, React, EF Core, MediatR, AutoMapper…
- ☁️ **Sẵn sàng triển khai trên Azure** thông qua Azure Developer CLI (azd).

---

## 📦 Cấu trúc dự án

Khi tạo dự án bằng template này, bạn sẽ nhận được cấu trúc thư mục theo **Clean Architecture**:

```
src/
 ├─ Application    # Chứa logic nghiệp vụ (Use Cases, CQRS - Command/Query)
 ├─ Domain         # Chứa các entity, giá trị, interface cơ bản
 ├─ Infrastructure # Chứa code giao tiếp với DB, service ngoài, implement repository
 ├─ Web            # ASP.NET Core Web API + (Angular/React nếu chọn SPA)
tests/
 ├─ Application.UnitTests
 ├─ Domain.UnitTests
 └─ Web.FunctionalTests
```

- **Domain** → chỉ chứa logic nghiệp vụ thuần tuý (Entities, ValueObjects, Exceptions).
- **Application** → chứa Use Case (Command/Query), Validation, Mapping.
- **Infrastructure** → chứa EF Core DbContext, Migration, Repository thực thi.
- **Web** → API controllers và giao diện Angular/React nếu chọn.

Cách tách này giúp code **độc lập framework**, **dễ test**, và **linh hoạt khi thay đổi công nghệ**.

---

## ⚡ Cách sử dụng

### 1. Cài đặt template
```bash
dotnet new install Clean.Architecture.Solution.Template
```

### 2. Tạo project mới

- **Với Angular**:
```bash
dotnet new ca-sln --client-framework Angular --output MyProject
```

- **Với React**:
```bash
dotnet new ca-sln -cf React -o MyProject
```

- **Chỉ API (không SPA)**:
```bash
dotnet new ca-sln -cf None -o MyProject
```

### 3. Chạy ứng dụng
```bash
cd src/Web
dotnet run
```

---

## 🗃️ Hỗ trợ cơ sở dữ liệu

Template hỗ trợ **SQL Server** (mặc định), **PostgreSQL** và **SQLite**.

Ví dụ chọn PostgreSQL:
```bash
dotnet new ca-sln --database postgresql
```

Tạo migration mới:
```bash
dotnet ef migrations add "InitialCreate" --project src/Infrastructure --startup-project src/Web --output-dir Data/Migrations
```

---

## 🧩 Tạo Use Case (Command/Query)

Template cung cấp sẵn **dotnet template** để tạo Use Case (CQRS):

- **Tạo Command**:
```bash
dotnet new ca-usecase --name CreateTodoList --feature-name TodoLists --usecase-type command --return-type int
```

- **Tạo Query**:
```bash
dotnet new ca-usecase -n GetTodos -fn TodoLists -ut query -rt TodosVm
```

---

## ☁️ Triển khai lên Azure

Đã tích hợp sẵn Azure Developer CLI:

```bash
azd auth login   # Đăng nhập Azure
azd up           # Tự động provision & deploy
```

---

## 🔧 Công nghệ chính được dùng

- **ASP.NET Core 9** – API backend
- **Entity Framework Core 9** – ORM
- **Angular 18 / React 18** – Frontend SPA
- **MediatR** – CQRS & Mediator pattern
- **AutoMapper** – Mapping DTO <-> Entity
- **FluentValidation** – Validation
- **NUnit, FluentAssertions, Moq, Respawn** – Testing

---

## 🏆 Lợi ích khi dùng template này

✅ **Nhanh chóng**: Tạo kiến trúc chuẩn chỉ trong vài giây.  
✅ **Dễ mở rộng**: Clean Architecture giúp tách biệt các tầng.  
✅ **Testable**: Có sẵn cấu trúc Unit Test và Functional Test.  
✅ **Hỗ trợ SPA**: Angular hoặc React tích hợp sẵn với ASP.NET Core.  
✅ **Triển khai dễ dàng**: Sẵn sàng chạy trên Azure.  

---

### 👉 Nói ngắn gọn

`Clean Architecture Solution Template` là **bộ khung tiêu chuẩn** cho ứng dụng ASP.NET Core (Web API hoặc SPA với Angular/React). Nó giúp bạn:

- Tiết kiệm thời gian setup kiến trúc ban đầu.
- Viết code chuẩn theo **Clean Architecture**.
- Tích hợp sẵn database, migration, test, và deployment Azure.

---

Bạn có muốn mình vẽ sơ đồ **kiến trúc tổng quan** của template này (Domain → Application → Infrastructure → Web) để dễ hình dung hơn không?