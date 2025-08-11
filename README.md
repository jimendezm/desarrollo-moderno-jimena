# LABORATORIO 1
## Realizado por: Jimena Méndez

## 1. Frameworks de desarrollo web

### a. ¿Qué es un framework y qué problema resuelve?
Se define como una estructura para realizar código de una forma más limpia y organizada de tal forma que se cumpla con ciertos modelos para mejor utilización de recursos y de los datos.

### b. Arquitectura general y enfoque (MVC, SPA, SSR, etc.).
Se utiliza en un determinado framework igualmente para estucturar el código con un patron de tal forma que haga que la separación de cada uno sean archivos para una determinada, como en el modelo MVC que separamos los modelos de los controladores y las vistas, dado que cada uno de ellos tiene una funcionalidad distinta pero el mismo objetivo.

### c. Ejemplo práctico documentado (estructura de proyecto, fragmento de código comentado).
Mini sistema de mensajería con ASP.NET Core (Razor Pages)

Un proyecto muy simple donde podamos mostrar mensajes que alguien envía (sin base de datos real, todo será de ejemplo), la arquitectura utilizada no es completamente MVC, Razor Pages tiene un enfoque a las paginás, cada archivo `.cshtml.cs` tiene su pagina y lógica.

- Modelos: Tiene la clase `Mensaje` que define cómo es un mensaje.
- Paginas: Tiene las páginas web (`.cshtml`) y su lógica (`.cshtml.cs`).

**Modelos/Mensaje.cs**
```csharp
namespace ProyectoMensajes.Models
{
    public class Mensaje
    {
        public string Usuario { get; set; } // Quién envía el mensaje
        public string Contenido { get; set; } // El texto del mensaje
        public DateTime Fecha { get; set; } // Cuándo se envió
    }
}
```

### d. Comparación breve entre al menos dos frameworks (según lenguaje o  enfoque).

Entre los más populares en la actualidad son React y .NET. Con React puedes poner todo como tú quieras y hasta inventar tu propia forma de trabajar. En .NET, en cambio, todo ya viene medio armado y tienes que adaptarte. También usan lenguajes diferentes: React con JavaScript y .NET con C#.

## 2. Control de versiones y trabajo colaborativo
### a. ¿Qué es el control de versiones y por qué es esencial?
Es escencial porque cuando se trabaja en un determinado proyecto con una gran comunidad, es necesario realizar el manejo de versiones de los proyectos, ya que este se basa en siempre hacer una actualización (commits) que son necesarios para mejorarlo y realizarlo hasta que ya este completo.

### b. Conceptos clave: repositorio, commit, branch, merge, pull request.
 Repositorio: Es útil para realizar un determinado proyecto y dentro de este hacer todas las actualizaciones.
- Commit: Guardar un cambio o actualización con un mensaje para recordar qué hiciste.
- Branch: Normalmente se utiliza como una copia del proyecto para trabajar sin dañar la el proyecto en la rama de origen.
- Merge: Juntar un nuevo cambio con los de otras actualizaciones que se han hecho en el proyecto.
- Pull Request: Como lo dice la palabra es una solicitud para pedir permiso para que tus cambios entren al proyecto oficial.

### c. Flujos de trabajo comunes (Git Flow, trunk-based, feature branches).
Estos flujos son altamente utilizados en proyectos complejos, que requieren de un alto control entre las actualizaciones que se vayan realizando. Entre ellos encontramos los siguientes:
- Git Flow: Utiliza varias ramas para diferentes propósitos del proyecto, entre esos se encuentran: `main`, `develop`, `feature`, `release` y `hotfix`.
- trunk-based: Todos trabajan sobre la rama principal y hacen cambios pequeños en un corto tiempo en ramas específicas.
- feature branches: Siempre se trabaja una sola funcionalidad en una rama y luego se actualiza en la principal.

### d. Ejemplo de cómo usar Git en un proyecto (inicialización, commits, ramas).
Para no utilizar muchas imagenes mostraré como se puede hacer en comandos:

- Para inicializar el repositorio se utiliza el comando 
```bash 
git init
```
- Para hacer el commit
```bash 
git commit -m "Primer commit"
```
- Para crear una nueva rama
```bash 
git branch nueva-funcion
```

- Volver a la rama principal y unir cambios
```bash 
git checkout main
git merge nueva-funcion
```
Aunque hay varios comandos para diferentes funcionalidades estos son los principales para inicialización, commits, ramas.

### e. Herramientas recomendadas (GitHub, GitLab, Bitbucket)
Entre las herramientas más utilizadas para el control de versiones podemos encontrar:
- GitHub: En lo personal, la más utilizada para mi y en la industria, es completamente gratuita y tiene una gran comunidad.
- GitLab: Solo hable de esta una vez y esta más orientado a proyectos más complejos y empresariales.
- Bitbucket: Muy usado en entornos corporativos y con Jira.

## 3. Autenticación y seguridad moderna
### a. Conceptos: autenticación, autorización, tokens, JWT, OAuth.
- Autenticación: Normalmente utilizada para acceder a sitios, entonces se utiliza para comprobar que un usuario externo puede acceder a un programa especifico.
- Autorización: Si el usuario externo ingresa, se le habilitan ciertos accesos dependiendo del rol que ocupe.
- Token: Es como un identificador para probar que iniciaste sesión.
- JWT: Un tipo de token con información codificada que el servidor puede leer. 
- OAuth: Un sistema para iniciar sesión usando otra cuenta (Google, Facebook, Apple). 

### b. Diagrama de flujo explicativo del proceso de autenticación con JWT.
![Diagrama JWT](https://www.mermaidchart.com/app/projects/4ccfc5bc-a662-4937-bf48-0d2ddd5c5dbd/diagrams/eba75619-a883-4123-b962-adaa91cf8d27/version/v0.1/edit)

### c. Buenas prácticas en seguridad web.
- Cerrar sesión después de un rato inactivo.
- Guardar contraseñas cifradas.  
- Usar HTTPS para que la información viaje segura.  
- No poner datos sensibles en el frontend.  

### d. Aplicaciones reales en plataformas modernas.
- Netflix: Te autenticas una vez y te mantiene conectado usando tokens.  
- Gmail: Usa OAuth para iniciar con tu cuenta de Google en otros servicios.  
- Facebook: Controla qué apps pueden usar tu información con autorización. 

## 4. Gestores de contenido desacoplados (Headless CMS)
### a. Definición de Headless CMS vs CMS tradicional.
El CMS tradicional manda el contenido directo a su página web. En cambio, el Headless solo guarda la información y te la envía, y tú decides si la pones en una web o una app.  

### b. Arquitectura basada en APIs.
En un Headless CMS, el contenido vive en un servidor y lo pides con **APIs**. No importa si usas React, Angular, .NET o cualquier otra cosa; la API manda la info y la acomodas en el frontend.  

### c. Ventajas, limitaciones y casos de uso comunes.
- Entre las ventajas es que es muy flexible porque se pueden mostrar desde cualquier dispositivo, y se puede cambiar el diseño sin tocar el contenido.
- Entre las limitaciones se tiene que saber programar para mostrar el contenido.
- Y entre los casos comunes son aplicaciones móviles, sitios web y demas.

### d. Ejemplo de cómo se conecta el frontend a un CMS headless.

Ejemplo con JavaScript y Fetch API para obtener artículos desde un CMS Headless (Strapi, por ejemplo):

```javascript
fetch('https://mi-cms-headless.com/api/articulos')
  .then(response => response.json())
  .then(data => {
    data.forEach(articulo => {
      console.log(articulo.titulo, articulo.contenido);
    });
  })
  .catch(error => console.error('Error al cargar artículos:', error));
```

## 5. Pasarelas de pago en aplicaciones web
### a. ¿Qué es una pasarela de pago? ¿Qué rol cumple en una aplicación moderna?
Es un intermediario entre tu app y el banco. Cuando alguien compra algo, la pasarela se encarga de validar los datos, asegurarse de que hay plata y mandarla al vendedor. Básicamente, evita que tengas que lidiar directamente con los bancos.

### b. Requisitos comunes: cuenta de comercio, seguridad, integración técnica.

- Necesitas registrarte en la pasarela y que te aprueben.
- Tienes que usar HTTPS.
- Programa la página web para que se conecte con la pasarela, lgunas tienen APIs fáciles.

### c. Ventajas y limitaciones de integrar pagos en línea.
Ventajas: La gente puede pagar fácil porque es muy accesible a todo tipo de clases, tambié automatizas cobros y son totalmente seguros.

Limitaciones: Las comisiones te pueden comer parte de las ganancias y algo muy importante es que requiere mantenimiento.

### d. Comparación entre al menos dos pasarelas (ej. Stripe, TiloPay, Bancos, etc.)
Entre las más conocidas Stripe vs PayPal:
- Stripe: Más para desarrolladores (API flexible), pero no está en todos los países.
- PayPal: Más conocido, pero tiene fees más altos y a veces congela cuentas sin explicación.

## 6. Automatización del despliegue y hosting moderno
### a. ¿Qué es CI/CD y por qué se usa en desarrollo web?
El CI/CD es como un "robot asistente" que te ayuda a probar y subir cambios de tu código sin morir en el intento. CI (Integración Continua) revisa automáticamente si tu código tiene errores al hacer un commit, y CD (Despliegue Continuo) lo sube al servidor si todo está bien.


### b. Hosting estático vs dinámico.
Estático: Para páginas web simples y solo usa HTML, CSS y JS. 
Dinámico: Para apps con bases de datos y usuarios (como una red social).

### c. Flujo de despliegue automatizado.
- Haces un cambio en tu código y lo subes a GitHub.
- El CI (ej: GitHub Actions) ejecuta tests automáticos.
- Si todo pasa, el CD despliega los cambios en el servidor.

### d. Documentar el proceso seguido para desplegar la parte 2 del laboratorio
1. Primero cree el repositorio con el comando: 
```bash 
git init
```
2. Hice un commit llamado `Laboratorio1` con los comandos: 
```bash
git add .
git commit -m "Laboratorio1" 
```
3. Subí el commit (push) desde el GitHub Desktop.
4. Inicie sesion de mi cuenta de GitHub en Netlify.
5. Subí el repositorio y me creó la siguiente URL: 
[Visita mi sitio](https://tubular-griffin-2506bf.netlify.app/)