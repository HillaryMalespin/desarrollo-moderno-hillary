# Laboratorio 1

## Frameworks de desarrollo web

   ### a. ¿Qué es un framework y qué problemas resuelve?
            Un framework es un esquema o marco de trabajo que ofrece una estructura base para 
            elaborar un proyecto con objetivos específicos, una especie de plantilla que sirve 
            como punto de partida para la organización y desarrollo de software.

            Utilizar frameworks puede simplificar una tarea o proceso, de ahí que se trate de una 
            de las herramientas habituales que manejan los Digital Workers, porque les ayuda a ser 
            más ágiles y productivos

            Nos ayuda a reducir el tiempo de produccion de un proyecto, agiliza proceso y se puede
            reutilizar muchas herramientas lo que nos ayuda a solventar muchos problemas.

   ### b. Arquitectura general y enfoque (MVC, SPA, SSR, etc.). 
            La mayoría de los frameworks usan una estructura conocida como arquitectura 
            MVC (Model-View-Controller). Esta arquitectura separa los componentes de una 
            aplicación en 3 grupos distintos: modelo, vista y controlador.
            
            La arquitectura MVC se implementó principalmente en el lado del servidor, con 
            el cliente solicitando actualizaciones a través de formularios o enlaces, y 
            recibiendo vistas actualizadas para mostrar en el navegador.

            La *capa modelo* es la que se encarga de manipular los datos
            La *capa vista* es la responsable de generar la interfaz de la aplicación (pantallas, páginas, etc.).
            La *capa controladora* actúa como intermediario entre el usuario y la capa modelo

   ### c. Ejemplo práctico documentado (estructura de proyecto, fragmento de codigo comentado)
   ### Estructura del proyecto 
            /mvc-example
            /models
                Product.php 
            /views
                products.php
            /controllers
                ProductController.php
            index.php
### Fragmento de codigo comentado

```javascript
    //Modelo
    class Product {
        public function getAllProducts() {
            // Simulación de datos (en producción, usa una base de datos real)
            return [
                ['id' => 1, 'name' => 'Producto A', 'price' => 10.00],
                ['id' => 2, 'name' => 'Producto B', 'price' => 15.50],
            ];
        }
    }
```
```javascript
//Controlador
require_once 'models/Product.php';

class ProductController {
    public function index() {
        $model = new Product();
        $products = $model->getAllProducts();
        require_once 'views/products.php';
    }
}
```

```javascript
//Vista
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Lista de Productos</title>
    <style> ul { list-style: none; } li { margin: 5px 0; } </style>
</head>
<body>
    <h1>Productos Disponibles</h1>
    <ul>
        <?php foreach ($products as $product): ?>
            <li><?php echo htmlspecialchars($product['name']) . " - $" . number_format($product['price'], 2); ?></li>
        <?php endforeach; ?>
    </ul>
</body>
</html>
```

   ### d. Comparación breve entre al menos dos frameworks (según lenguaje o enfoque). 
   ### ASP.NET MVC:
   ***Arquitectura:***
            ASP.NET MVC es un framework de Microsoft para construir aplicaciones web utilizando el patrón MVC. 
            Se integra con .NET Framework y .NET Core, permitiendo desarrollo multiplataforma. 
    ***Enfoque:***
            Se enfoca en la separación de preocupaciones, facilitando el desarrollo y mantenimiento de aplicaciones 
            web complejas. Ofrece flexibilidad y control sobre la estructura de la aplicación. 
    ***Ventajas:***
            **Flexibilidad:** Permite personalizar la forma en que se manejan las solicitudes, la lógica de negocio y la presentación. 
            **Facilidad de testing:** La separación de capas facilita la creación de pruebas unitarias y de integración. 
            **Comunidad y soporte:** Amplia comunidad y documentación, especialmente con ASP.NET Core. 
    ***Desventajas:***
            **Complejidad:** Puede resultar complejo para proyectos pequeños o simples debido a su flexibilidad. 
            **Curva de aprendizaje:** Requiere tiempo para dominar los conceptos y la estructura del framework. 

   ### Spring MVC:
   ***Arquitectura:***
            Spring MVC es un componente del framework Spring para Java, también basado en el patrón MVC.
   ***Enfoque:***
            Similar a ASP.NET MVC, Spring MVC promueve la separación de preocupaciones y la modularidad en el desarrollo 
            de aplicaciones Java.
   ***Ventajas:***
            **Productividad:** Ofrece características como inyección de dependencias y soporte para desarrollo basado en 
            anotaciones, lo que agiliza el desarrollo.
            **Reutilización de código:** Facilita la reutilización de componentes y la creación de aplicaciones modulares.
            **Amplia comunidad y ecosistema:** Cuenta con una gran comunidad de desarrolladores Java y un ecosistema rico en 
            bibliotecas y herramientas.
   ***Desventajas:***
            **Curva de aprendizaje:** Similar a ASP.NET MVC, Spring MVC puede tener una curva de aprendizaje pronunciada 
            para nuevos usuarios.
            **Overhead:** El framework puede agregar complejidad y sobrecarga a proyectos pequeños. 

   ***Comparación:***
            ASP.NET MVC se basa en C# y .NET, mientras que Spring MVC se basa en Java. 

## Control de versiones y trabajo colaborativo

  ### a. ¿Qué es el control de versiones y por qué es esencial? 
            Es la práctica de rastrear y gestionar los cambios en el código de software. Los sistemas de control de 
            versiones son herramientas de software que ayudan a los equipos de software a gestionar los cambios en el 
            código fuente a lo largo del tiempo. 
 
   ### b. Conceptos clave: repositorio, commit, branch, merge, pull request. 

**Repositorio:** Un repositorio es un lugar donde se guarda y organiza información 
            digital, como documentos o archivos informáticos.

**Commit:** Se usa para guardar los cambios en el repositorio local. 
            Crea un nuevo objeto de confirmación, que actúa como una instantánea 
            de los archivos del proyecto en un momento dado. 

**Branch:** Las ramas de Git son un puntero eficaz para las instantáneas de 
            tus cambios. Cuando quieres 
            añadir una nueva función o solucionar un error, independientemente de su 
            tamaño, generas una nueva 
            rama para alojar estos cambios.

**Merge:** Permite tomar las líneas independientes de desarrollo creadas por git 
            branch e integrarlas en una sola rama.

**Pull request:** Se usa para cargar contenido del repositorio local a un repositorio 
            remoto. El envío es la forma de transferir confirmaciones desde tu repositorio local 
            a un repositorio remoto.

   ### c. Flujos de trabajo comunes (Git Flow, trunk-based, feature branches). 

**Gitflow:** Es un modelo alternativo de ramificación de Git que implica el uso de ramas 
            de características y múltiples ramas principales.

![Diagrama del gitflow](gitflow.png)

            Trunk-based: El desarrollo basado en tronco es una práctica de gestión de control de versiones en la que 
            los desarrolladores fusionan pequeñas actualizaciones de forma frecuente en un “tronco” o rama principal (main).
            Dado que esta práctica simplifica las fases de fusión e integración, ayuda a lograr la CI/CD (Continuous 
            Integration / Continuous Deployment, siendo estos la Integración Continua y Despliegue Continuo) y, al 
            mismo tiempo, aumenta la entrega de software y el rendimiento de la organización.

            Feature branches: La idea central del flujo de trabajo de rama de funciones es que todo el desarrollo de 
            funciones se realice en una rama dedicada, en lugar de en la mainrama principal. Esta encapsulación facilita 
            que varios desarrolladores trabajen en una función específica sin afectar el código base principal. Además, 
            significa que la mainrama nunca contendrá código defectuoso, lo cual supone una gran ventaja para los entornos 
            de integración continua.

   ### d. Ejemplo de cómo usar Git en un proyecto (inicialización, commits, ramas). 
            1. Iniciamos creando un proyecto en Github





# Fuentes
https://unirfp.unir.net/revista/ingenieria-y-tecnologia/framework/
https://www.ticportal.es/glosario-tic/framework-software#:~:text=La%20mayor%C3%ADa%20de%20los%20frameworks,encuentran%20los%20datos%20de%20dominio.
https://developer.mozilla.org/es/docs/Glossary/MVC
https://www.atlassian.com/es/git/tutorials/what-is-version-control 
https://www.atlassian.com/es/git/tutorials/rewriting-history
https://openwebinars.net/blog/trunk-based-development-vs-git-flow-cual-elegir/
