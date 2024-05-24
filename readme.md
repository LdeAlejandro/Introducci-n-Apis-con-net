

# Comandos usados en consola vs code

```sh
dotnet add package Microsoft.EntityFrameworkCore  
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Microsoft.EntityFrameworkCore.sqlserver
donet-ef migrations add CriacaoTabelaContato
dotnet-ef database update
dotnet watchrun
```


# .NET Commands Guide

## **Comandos para adicionar pacotes e gerenciar migrações com Entity Framework Core**

### **Adicionar pacotes do Entity Framework Core**

```sh
# Adiciona o pacote Microsoft.EntityFrameworkCore ao seu projeto .NET
dotnet add package Microsoft.EntityFrameworkCore

# Adiciona o pacote Microsoft.EntityFrameworkCore.Design ao seu projeto .NET, que contém ferramentas de design para o Entity Framework Core
dotnet add package Microsoft.EntityFrameworkCore.Design

# Adiciona o pacote Microsoft.EntityFrameworkCore.SqlServer ao seu projeto .NET, que permite o uso do SQL Server com o Entity Framework Core
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

### **Gerenciar migrações com Entity Framework Core**

```sh
# Adiciona uma nova migração chamada "CriacaoTabelaContato" ao seu projeto. As migrações são usadas para gerenciar alterações no esquema do banco de dados
dotnet-ef migrations add CriacaoTabelaContato

# Aplica as migrações pendentes ao banco de dados, atualizando-o para a versão mais recente do esquema definido no código
dotnet-ef database update

# Executa o projeto .NET e recompila automaticamente as alterações feitas no código durante o desenvolvimento
dotnet watch run
```

## Explicação dos Comandos

### **Adicionar pacotes do Entity Framework Core**

- `dotnet add package Microsoft.EntityFrameworkCore`: Este comando adiciona o pacote `Microsoft.EntityFrameworkCore` ao seu projeto .NET, que é o núcleo do Entity Framework Core, uma popular biblioteca de ORM (Mapeamento Objeto-Relacional).
    
- `dotnet add package Microsoft.EntityFrameworkCore.Design`: Este comando adiciona o pacote `Microsoft.EntityFrameworkCore.Design`, que contém ferramentas necessárias para a criação e gerenciamento de migrações de banco de dados e outras funcionalidades de design do Entity Framework Core.
    
- `dotnet add package Microsoft.EntityFrameworkCore.SqlServer`: Este comando adiciona o pacote `Microsoft.EntityFrameworkCore.SqlServer`, que permite que o Entity Framework Core se conecte e trabalhe com o banco de dados Microsoft SQL Server.
    

### **Gerenciar migrações com Entity Framework Core**

- `dotnet-ef migrations add CriacaoTabelaContato`: Este comando cria uma nova migração chamada `CriacaoTabelaContato`. As migrações no Entity Framework Core são usadas para gerenciar e aplicar alterações no esquema do banco de dados de maneira controlada e versionada.


    
- `dotnet-ef database update`: Este comando aplica todas as migrações pendentes ao banco de dados, sincronizando-o com o esquema de dados definido no código do seu projeto. Ele garante que o banco de dados esteja atualizado com a versão mais recente das migrações.
    
- `dotnet watch run`: Este comando executa o projeto .NET e monitora mudanças no código. Se algum arquivo for alterado, ele recompila e reinicia automaticamente a aplicação, facilitando o desenvolvimento contínuo e o feedback rápido.


# Doc Program.cs Introducción Apis con net

```markdown
# Configuração do `Program.cs` em um projeto ASP.NET Core

O arquivo `Program.cs` em um projeto ASP.NET Core é o ponto de entrada principal para a aplicação. Ele configura e inicializa o aplicativo web, adiciona os serviços necessários e define como os pedidos HTTP são tratados.

A seguir, é apresentada uma configuração típica do `Program.cs` para um projeto ASP.NET Core com suporte a Swagger/OpenAPI:

```csharp
var builder = WebApplication.CreateBuilder(args);

// Adiciona serviços ao contêiner.
builder.Services.AddControllers();

// Configura o Swagger/OpenAPI
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

var app = builder.Build();

// Configura o pipeline de requisição HTTP
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.UseHttpsRedirection();

app.UseAuthorization();

app.MapControllers();

app.Run();
```

## Explicação das Configurações

### Inicialização do WebApplication Builder

```csharp
var builder = WebApplication.CreateBuilder(args);
```

- `WebApplication.CreateBuilder(args)`: Inicializa um novo construtor de aplicativo web com os argumentos fornecidos. Este construtor é responsável por configurar todos os serviços e middleware necessários para a aplicação.

### Adicionando Serviços ao Contêiner

```csharp
// Adiciona serviços ao contêiner.
builder.Services.AddControllers();

// Configura o Swagger/OpenAPI
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();
```

- `builder.Services.AddControllers()`: Adiciona serviços de controle MVC ao contêiner de injeção de dependência, permitindo o uso de controladores na aplicação.
- `builder.Services.AddEndpointsApiExplorer()`: Adiciona suporte para a exploração de endpoints da API, que é uma parte necessária para configurar o Swagger/OpenAPI.
- `builder.Services.AddSwaggerGen()`: Adiciona o gerador Swagger, que produz documentação da API em conformidade com o Swagger/OpenAPI.

### Construindo o Aplicativo

```csharp
var app = builder.Build();
```

- `builder.Build()`: Constrói a aplicação utilizando as configurações definidas anteriormente.

### Configurando o Pipeline de Requisição HTTP

```csharp
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.UseHttpsRedirection();

app.UseAuthorization();

app.MapControllers();

app.Run();
```

- `if (app.Environment.IsDevelopment())`: Verifica se o ambiente atual é o de desenvolvimento.
    - `app.UseSwagger()`: Habilita o middleware Swagger para gerar a documentação da API.
    - `app.UseSwaggerUI()`: Habilita a interface do usuário Swagger para navegar pela documentação da API.
- `app.UseHttpsRedirection()`: Redireciona todas as solicitações HTTP para HTTPS, garantindo comunicações seguras.
- `app.UseAuthorization()`: Adiciona o middleware de autorização, garantindo que as rotas protegidas sejam acessadas apenas por usuários autorizados.
- `app.MapControllers()`: Mapeia as rotas dos controladores adicionados anteriormente para os endpoints apropriados.
- `app.Run()`: Executa a aplicação, iniciando o servidor web e ouvindo as solicitações HTTP.

---

Este documento fornece uma visão geral de como configurar e usar o `Program.cs` em um projeto ASP.NET Core, explicando a inicialização do aplicativo, a adição de serviços, e a configuração do pipeline de requisição HTTP.

# Doc UsuarioController.cs Introducción Apis con net

```markdown
# Configuração do `UsuarioController.cs` em um projeto ASP.NET Core

O arquivo `UsuarioController.cs` define um controlador API para gerenciar requisições HTTP relacionadas ao usuário. Este controlador possui duas ações: uma para obter a data e hora atuais e outra para apresentar uma mensagem de boas-vindas com o nome fornecido.

A seguir, é apresentada uma configuração típica do `UsuarioController.cs` para um projeto ASP.NET Core:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;

namespace Modulo_Api_dotnet_webApi.Controllers
{
    [ApiController]
    [Route("controller")]
    public class UsuarioController : ControllerBase
    {
        // Endpoint para obter a data e hora atuais
        [HttpGet("ObterDataHoraAtual")]
        public IActionResult ObterDataHora()
        {
            var obj = new
            {
                Data = DateTime.Now.ToLongDateString(),
                Hora = DateTime.Now.ToShortTimeString(),
            };
            return Ok(obj);
        }

        // Endpoint para apresentar uma mensagem de boas-vindas com o nome fornecido
        [HttpGet("Apresentar/{nome}")]
        public IActionResult Apresentar(string nome)
        {
            var mensagem = $"Olá {nome}, seja bem vindo!";
            return Ok(new { mensagem });
        }
    }
}
```

## Explicação das Configurações

### Using Directives

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
```

- `using System;`: Importa o namespace `System`, que contém tipos fundamentais como `DateTime`.
- `using Microsoft.AspNetCore.Mvc;`: Importa o namespace `Microsoft.AspNetCore.Mvc`, que fornece tipos e funcionalidades para criar controladores e manipular requisições HTTP.

### Definição da Classe `UsuarioController`

```csharp
namespace Modulo_Api_dotnet_webApi.Controllers
{
    [ApiController]
    [Route("controller")]
    public class UsuarioController : ControllerBase
    {
        // Métodos de ação aqui
    }
}
```

- `namespace Modulo_Api_dotnet_webApi.Controllers`: Define o namespace para o controlador, agrupando-o logicamente com outros controladores do projeto.
- `[ApiController]`: Indica que esta classe é um controlador de API. Esta anotação facilita várias funcionalidades, como a validação automática de modelos.
- `[Route("controller")]`: Define a rota base para as ações dentro deste controlador. O placeholder `"controller"` é substituído pelo nome do controlador sem o sufixo "Controller", ou seja, "Usuario".

### Método `ObterDataHora`

```csharp
[HttpGet("ObterDataHoraAtual")]
public IActionResult ObterDataHora()
{
    var obj = new
    {
        Data = DateTime.Now.ToLongDateString(),
        Hora = DateTime.Now.ToShortTimeString(),
    };
    return Ok(obj);
}
```

- `[HttpGet("ObterDataHoraAtual")]`: Define que este método responde a requisições HTTP GET na rota `ObterDataHoraAtual`.
- `IActionResult ObterDataHora()`: Método de ação que retorna a data e hora atuais.
- `DateTime.Now.ToLongDateString()`: Obtém a data atual em um formato de string longa.
- `DateTime.Now.ToShortTimeString()`: Obtém a hora atual em um formato de string curta.
- `return Ok(obj);`: Retorna um status HTTP 200 (OK) com o objeto contendo a data e hora atuais.

### Método `Apresentar`

```csharp
[HttpGet("Apresentar/{nome}")]
public IActionResult Apresentar(string nome)
{
    var mensagem = $"Olá {nome}, seja bem vindo!";
    return Ok(new { mensagem });
}
```

- `[HttpGet("Apresentar/{nome}")]`: Define que este método responde a requisições HTTP GET na rota `Apresentar/{nome}`, onde `{nome}` é um parâmetro de rota.
- `IActionResult Apresentar(string nome)`: Método de ação que retorna uma mensagem de boas-vindas usando o nome fornecido na rota.
- `var mensagem = $"Olá {nome}, seja bem vindo!";`: Cria uma mensagem de boas-vindas personalizada.
- `return Ok(new { mensagem });`: Retorna um status HTTP 200 (OK) com o objeto contendo a mensagem de boas-vindas.

---

Este documento fornece uma visão geral de como configurar e usar o `UsuarioController.cs` em um projeto ASP.NET Core, explicando a definição de controladores, rotas e métodos de ação para manipulação de requisições HTTP.

# Doc appsettings.json Introducción Apis con net

```markdown
# Configuração do `appsettings.json` em um projeto .NET

O arquivo `appsettings.json` é usado para armazenar configurações de aplicativos em projetos .NET, especialmente aqueles que utilizam o ASP.NET Core. Este arquivo permite definir configurações em um formato estruturado e fácil de ler, geralmente em JSON. 

A seguir, é apresentada uma configuração típica do `appsettings.json`:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*"
}
```

## Explicação das Configurações

### Logging

A seção `Logging` é usada para configurar como o aplicativo registra (ou loga) informações. O registro é uma parte crucial do monitoramento e depuração de aplicações. 

#### LogLevel

Dentro da seção `Logging`, a subseção `LogLevel` especifica os níveis de log para diferentes partes do aplicativo:

- `"Default": "Information"`: Define o nível de log padrão como "Information". Isso significa que todas as mensagens de log com nível "Information" ou superior (como "Warning", "Error", e "Critical") serão registradas.
- `"Microsoft.AspNetCore": "Warning"`: Define o nível de log para o namespace `Microsoft.AspNetCore` como "Warning". Isso significa que apenas mensagens de log com nível "Warning" ou superior para componentes do ASP.NET Core serão registradas.

Os níveis de log em ordem crescente de severidade são: 
1. Trace
2. Debug
3. Information
4. Warning
5. Error
6. Critical
7. None (para desativar o registro de log)

### AllowedHosts

A configuração `AllowedHosts` especifica quais hosts são permitidos para acessar a aplicação. Isso é útil para a segurança, especialmente em ambientes de produção:

- `"AllowedHosts": "*"`: O valor `*` indica que todos os hosts são permitidos. Em um ambiente de produção, é recomendável restringir os hosts permitidos para melhorar a segurança, especificando uma lista de nomes de domínio.

## Uso do `appsettings.json`

Em um projeto ASP.NET Core, o `appsettings.json` é carregado automaticamente durante a inicialização do aplicativo. O conteúdo do arquivo pode ser acessado e utilizado através da injeção de dependência ou diretamente via `Configuration` no `Startup.cs`.

### Exemplo de uso em `Startup.cs`

```csharp
public class Startup
{
    public IConfiguration Configuration { get; }

    public Startup(IConfiguration configuration)
    {
        Configuration = configuration;
    }

    public void ConfigureServices(IServiceCollection services)
    {
        // Configurar serviços aqui
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
            app.UseHsts();
        }

        app.UseHttpsRedirection();
        app.UseStaticFiles();

        app.UseRouting();

        app.UseAuthorization();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapControllerRoute(
                name: "default",
                pattern: "{controller=Home}/{action=Index}/{id?}");
        });

        // Exemplo de como usar uma configuração do appsettings.json
        var logLevel = Configuration["Logging:LogLevel:Default"];
        Console.WriteLine($"Default LogLevel: {logLevel}");
    }
}
```

Neste exemplo, a configuração de nível de log padrão é lida do `appsettings.json` e exibida no console.

---

Este documento fornece uma visão geral de como configurar e usar o `appsettings.json` em um projeto .NET, facilitando o gerenciamento de configurações de forma organizada e centralizada.

# Doc appsettings.Development.json Apis con net

```markdown
# Configuração do `appsettings.Development.json` em um projeto .NET

O arquivo `appsettings.Development.json` é usado para armazenar configurações específicas para o ambiente de desenvolvimento em projetos .NET, especialmente aqueles que utilizam o ASP.NET Core. Este arquivo permite que você tenha configurações diferentes para ambientes distintos (desenvolvimento, produção, etc.) sem a necessidade de alterar o código-fonte.

A seguir, é apresentada uma configuração típica do `appsettings.Development.json`:

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  }
}
```

## Explicação das Configurações

### Logging

A seção `Logging` é usada para configurar como o aplicativo registra (ou loga) informações. O registro é uma parte crucial do monitoramento e depuração de aplicações.

#### LogLevel

Dentro da seção `Logging`, a subseção `LogLevel` especifica os níveis de log para diferentes partes do aplicativo:

- `"Default": "Information"`: Define o nível de log padrão como "Information". Isso significa que todas as mensagens de log com nível "Information" ou superior (como "Warning", "Error", e "Critical") serão registradas.
- `"Microsoft.AspNetCore": "Warning"`: Define o nível de log para o namespace `Microsoft.AspNetCore` como "Warning". Isso significa que apenas mensagens de log com nível "Warning" ou superior para componentes do ASP.NET Core serão registradas.

Os níveis de log em ordem crescente de severidade são: 
1. Trace
2. Debug
3. Information
4. Warning
5. Error
6. Critical
7. None (para desativar o registro de log)

## Uso do `appsettings.Development.json`

Em um projeto ASP.NET Core, o `appsettings.Development.json` é carregado automaticamente durante a inicialização do aplicativo quando o ambiente é configurado como "Development". O conteúdo do arquivo pode ser acessado e utilizado através da injeção de dependência ou diretamente via `Configuration` no `Startup.cs`.

### Exemplo de uso em `Startup.cs`

```csharp
public class Startup
{
    public IConfiguration Configuration { get; }

    public Startup(IConfiguration configuration)
    {
        Configuration = configuration;
    }

    public void ConfigureServices(IServiceCollection services)
    {
        // Configurar serviços aqui
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
            app.UseHsts();
        }

        app.UseHttpsRedirection();
        app.UseStaticFiles();

        app.UseRouting();

        app.UseAuthorization();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapControllerRoute(
                name: "default",
                pattern: "{controller=Home}/{action=Index}/{id?}");
        });

        // Exemplo de como usar uma configuração do appsettings.Development.json
        var logLevel = Configuration["Logging:LogLevel:Default"];
        Console.WriteLine($"Default LogLevel: {logLevel}");
    }
}
```

Neste exemplo, a configuração de nível de log padrão é lida do `appsettings.Development.json` e exibida no console.

---

Este documento fornece uma visão geral de como configurar e usar o `appsettings.Development.json` em um projeto .NET, facilitando o gerenciamento de configurações específicas para o ambiente de desenvolvimento de forma organizada e centralizada.
