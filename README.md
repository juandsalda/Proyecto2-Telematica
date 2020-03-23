## Definición de Equipo (integrantes, emails)
@Author: Juan Diego Saldarriaga @Email: jsalda23@eafit.edu.co

@Author: Alejandro Diaz Cano @Email: adiazc@eafit.edu.co

## Asignación de roles y responsabilidades de cada integrante del equipo en el desarrollo del proyecto2.

#### Juan Diego Saldarriaga: 
  - Responsable del despliegue en AWS
  - Responsable de rendimiento
  - Responsable de seguridad

#### Alejandro Diaz Cano:
  - Responsable del despliegue en DCA
  - Responsable de Disponibilidad


## Especificación de requisitos no funcionales.

### Disponibilidad
### Rendimiento

Las pruebas de rendimiento son un conjunto de pruebas no funcionales que se realizan, para determinar la velocidad de ejecución de una tarea concreta en un sistema bajo condiciones particulares de trabajo.

Los objetivos de estas pruebas son:

    Validar y verificar atributos de la calidad del sistema: uso de los recursos, escalabilidad y fiabilidad.
    Comparación de sistemas para encontrar cuál de ellos funciona mejor.
    Determinar qué componentes del sistema provocan que el conjunto .presente rendimientos bajos.

Tipos de Pruebas de Rendimiento

1. Prueba de Carga => Load Test

Prueba de rendimiento que se realiza para observar el comportamiento de una aplicación bajo una cantidad de peticiones esperada.

Objetivos:
    Mostrar los tiempos de respuesta de todas las transacciones importantes.
    Localizar los ‘cuellos de botella’ de una aplicación.

2. Pruebas de Estrés => Stress Test

Prueba de rendimiento que se realiza para observar el comportamiento de una aplicación bajo una cantidad de peticiones extrema.

Objetivos:

    ‘Romper’ la aplicación.
    Determinar cómo rendirá la aplicación si la carga real supera a la carga esperada

3.  Otras Pruebas: de picos, de estabilidad, …

A la hora de efectuar pruebas de rendimiento empleando herramientas de software, es necesario que el departamento de QA, defina un escenario lo más real posible, es decir, lo más semejante a las situaciones de funcionamiento en el entorno.
* __Patrones y mejores prácticas__

    * __Pensar en Caché:__ Tener almacenamiento en cache, es decir, tener la mayor cantidad
    posible de componentes y paginas importantes bajo una estrategia de almacenamiento en caché.

    * __Diseño para el fracaso:__ Evaluar todas las posibilidades de fracaso y su probabilidad probable.
    Algunos eventos comunes de falla pueden ser fallos de hardware, fallos de seguridad,
    desastres naturales, repunte repentino del tráfico de usuarios, fallos de red, fallos de operaciones, etc.

    * __Computación distribuida y paralela:__ Diseñe software para que su computación pueda
    distribuirse a través de múltiples nodos de computación. Esto ofrece la doble ventaja de rendimiento y escalabilidad.

    * __Mantenerse liviano:__ los componentes páginas clave deben mantenerse ligeros reduciendo
    su tamaño general y minimizando el número de viajes de ida y vuelta del servidor.

    * __Cargas no bloqueadas usando la solicitud de datos asincrónicos:__ Sean componentes del
    lado del cliente o para comunicarse con el servidor o para la agregación de datos, intente
    aprovechar el enfoque basado en AJAX. Esto mejora drásticamente el tiempo de carga de la
    página percibida y proporciona una carga no bloqueante de la página.

    * __Usar la política de carga bajo demanda:__* Cargue los datos y el componente sólo cuando sea necesario.

    * __Batching:*__ Mientras se recuperan datos de sistemas de interfaz como una base de datos
    o servicios web, se recomienda hacer batch de las solicitudes con el fin de minimizar el
    número de viajes de ida y vuelta del servidor.

### Seguridad

La seguridad de aplicaciones web es una rama de la Seguridad Informática que se encarga específicamente de la seguridad de sitios web, aplicaciones web y servicios web.

A un alto nivel, la seguridad de aplicaciones web se basa en los principios de la seguridad de aplicaciones pero aplicadas específicamente a la World Wide Web.
*https://es.wikipedia.org/wiki/Seguridad_de_aplicaciones_web*

* __Patrones y mejores prácticas__

    * __Balancear riesgo y usabilidad:__ A mayor complejidad de nuestro sitio, aumenta el riesgo de que se sufra un ataque debido a sus características más elaboradas, es por eso que deben considerarse opciones de seguridad necesarias y sencillas pero eficientes, que ayuden a mitigar cualquier característica que la haga vulnerable.

    * __Rastrear el paso de los datos:__  En las aplicaciones web, existen maneras de distinguir los orígenes de los datos y poder así reconocer cuando los datos pueden ser dignos de confianza y cuando no.

    * __Filtrar entradas:__ El filtrado es una de las piedras angulares de la seguridad en aplicaciones web. Es el proceso por el cual se prueba la validez de los datos. Si nos aseguramos que los datos son filtrados apropiadamente al entrar, podemos eliminar el riesgo de que datos contaminados sean usados para provocar funcionamientos no deseados en la aplicación.

    * __Escapado de salidas:__ Codificar o decodificar caracteres especiales de tal forma que su significado original sea preservado. Si llegamos a utilizar una codificación en particular es necesario conocer los caracteres reservados los cuales serán necesarios escapar.
    


## Qué patrones de arquitectura específicos (patrones de escalabilidad y buenas prácticas) se utilizarán en el SISTEMA para apoyar esta escalabilidad:

### Mejores prácticas
#### - DRY(Don’t repeat yourself):
Eliminar la duplicación de logica de negocio a partir de la abstracción, permitir la automatización de procesos y evitar la repetición de código, la duplicación es dificil de mantener y genera proyectos mas complejos y pesados.

#### - KISS(Keep It Simple Stupid): 
Mantener la simplicidad como objetivo principal en el diseño de#### - la aplicación y asi evitar la complejidad.

#### - YAGNI(You ain't gonna need it): 
No implementar nada a partir de supuesto, es decir, estar seguros de implementar para ahorranos tiempo y esfuerzo.

#### - Pruebas continuas: 
Evaluar el funcionamiento de la aplicación en ambientes de pruebas antes de lanzar un avanzo a producción.

#### -Uso de repositorio

### Selección de tácticas 

### Decisiones de diseño 

### Definición de Herramientas a utilizar

## Referencias

  - Seguridad de aplicaciones web - https://es.wikipedia.org/wiki/Seguridad_de_aplicaciones_web
  - Modelo–vista–controlador - https://es.wikipedia.org/wiki/Modelo%E2%80%93vista%E2%80%93controlador
  - Aspectos Básicos de la Seguridad en Aplicaciones Web - https://www.seguridad.unam.mx/historico/documento/index.html-id=17
  - Escenarios de calidad - https://github.com/Arquisoft/ObservaTerra11/wiki/Escenarios-de-calidad
  - Don’t Repeat Yourself - https://deviq.com/don-t-repeat-yourself/
  - Principio KISS: De qué se trata (Parte 1) - https://mantenlosimple.com/2013/10/12/principio-kiss-p1/
  - “Architecting High Performing, Scalableand Available Enterprise Web Applications” de Shailesh Kumar, 2015 -     http://proquestcombo.safaribooksonline.com.ezproxy.eafit.edu.co/book/software-engineering-and-development/enterprise/9780128022580/firstchapter
  - Pruebas de rendimiento - https://www.fractaliasystems.com/pruebas-de-rendimiento-quality-assurance/

