# Doc Program.cs Introducción Apis con net

Este código es parte de una configuración básica de una aplicación ASP.NET Core utilizando el enfoque de punto de entrada único (`Program.cs`). Aquí hay una explicación detallada:

1. `var builder = WebApplication.CreateBuilder(args);`:
    
    - `WebApplication.CreateBuilder(args)` es un método estático que crea un nuevo constructor de aplicaciones web. Toma los argumentos de la línea de comandos (`args`) y los utiliza para configurar el constructor de la aplicación.
    - `builder` es un objeto que se utiliza para configurar y construir la aplicación.
2. `builder.Services.AddControllers();`:
    
    - Agrega el servicio de controladores a la colección de servicios de la aplicación.
    - Este servicio permite que la aplicación ASP.NET Core tenga controladores que respondan a las solicitudes HTTP.
3. `builder.Services.AddEndpointsApiExplorer();`:
    
    - Agrega el servicio del explorador de API de puntos finales a la colección de servicios de la aplicación.
    - Este servicio proporciona la capacidad de explorar y documentar los puntos finales de la API en tiempo de ejecución.
4. `builder.Services.AddSwaggerGen();`:
    
    - Agrega el generador de Swagger a la colección de servicios de la aplicación.
    - Swagger es una herramienta que permite documentar, probar e interactuar con API REST.
5. `var app = builder.Build();`:
    
    - Construye la aplicación utilizando la configuración proporcionada por el constructor (`builder`).
6. Configuración del pipeline de solicitud HTTP:
    
    - `if (app.Environment.IsDevelopment()) { ... }`: Verifica si la aplicación se está ejecutando en un entorno de desarrollo.
    - `app.UseSwagger();` y `app.UseSwaggerUI();`: Habilita Swagger y su interfaz de usuario Swagger UI para la documentación de la API. Estos middleware solo se habilitan en el entorno de desarrollo.
    - `app.UseHttpsRedirection();`: Redirige las solicitudes HTTP a HTTPS.
    - `app.UseAuthorization();`: Agrega middleware para configurar la autorización.
    - `app.MapControllers();`: Asocia los controladores de la aplicación con las rutas de los puntos finales de la API.
7. `app.Run();`:
    
    - Inicia la aplicación, haciendo que escuche las solicitudes HTTP entrantes y las maneje según la configuración del pipeline de solicitud HTTP.


```c#

var builder = WebApplication.CreateBuilder(args);

// Add services to the container.
builder.Services.AddControllers();

// Learn more about configuring Swagger/OpenAPI at https://aka.ms/aspnetcore/swashbuckle
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

var app = builder.Build();

// Configure the HTTP request pipeline.
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
# Doc UsuarioController.cs Introducción Apis con net


Este código define un controlador de API en ASP.NET Core que maneja las solicitudes relacionadas con los usuarios. Aquí está la documentación:

1. `using Microsoft.AspNetCore.Mvc;`: Este espacio de nombres proporciona clases y métodos para crear y manejar controladores en ASP.NET Core.
    
2. `namespace Modulo_Api_dotnet_webApi.Controllers`: Define un espacio de nombres llamado `Modulo_Api_dotnet_webApi.Controllers`, que contiene la definición del controlador de la API.
    
3. `[ApiController]`: Un atributo de marcador que indica que la clase es un controlador de API. Esto habilita varios comportamientos por defecto, como la validación de modelo y la respuesta automática de códigos de estado HTTP.
    
4. `[Route("controller")]`: Especifica la ruta base para las solicitudes que se dirigen a este controlador. En este caso, todas las rutas se basarán en `/controller`.
    
5. `public class UsuarioController : ControllerBase`: Define una clase llamada `UsuarioController` que hereda de `ControllerBase`, lo que indica que es un controlador de API.
    
6. `[HttpGet("ObterDataHoraAtual")]`: Especifica que este método debe responder a las solicitudes HTTP GET en la ruta relativa `/controller/ObterDataHoraAtual`.
    
7. `public IActionResult ObterDataHora()`: Define un método llamado `ObterDataHora` que devuelve un `IActionResult`. Este método se llama cuando se realiza una solicitud HTTP GET a `/controller/ObterDataHoraAtual`.
    
8. Dentro de `ObterDataHora()`, se crea un objeto anónimo que contiene la fecha y hora actual en formato largo y corto.
    
9. `return Ok(obj);`: Devuelve una respuesta HTTP 200 (OK) junto con el objeto creado en el paso anterior.
    
10. `[HttpGet("Apresentar/{nome}")]`: Especifica que este método debe responder a las solicitudes HTTP GET en la ruta relativa `/controller/Apresentar/{nome}`, donde `{nome}` es un parámetro de ruta que acepta una cadena.
    
11. `public IActionResult Apresentar(string nome)`: Define un método llamado `Apresentar` que acepta un parámetro `nome` de tipo `string`. Este método se llama cuando se realiza una solicitud HTTP GET a `/controller/Apresentar/{nome}`.
    
12. Dentro de `Apresentar()`, se crea un mensaje de saludo utilizando el nombre proporcionado en el parámetro `nome`.
    
13. `return Ok(new { mensagem });`: Devuelve una respuesta HTTP 200 (OK) junto con un objeto anónimo que contiene el mensaje de saludo creado en el paso anterior.
```c#
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
        
        [HttpGet("Apresentar/{nome}")]
        public IActionResult Apresentar(string nome)
        {
            var mensagem = $"Olá {nome}, seja bem vindo!";
            return Ok(new{mensagem});
        }
    }
}
```
