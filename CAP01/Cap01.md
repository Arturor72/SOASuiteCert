SOA: provee una arquitectura empresarial que soporta la construccion y coneccion
de aplicaciones que proveen soluciones a problemas de negocio. Facilita el
desarrollo de aplicaciones como web services de negocio modulares, que pueden 
ser facil de integrar y rehusar, creando una Infraestructura de TI adaptable.

Oracle SOA Suite: Provee de componentes para diseñar, desplegar y administrar
aplicaciones compuestas, habilita la creacion, administracion y orquestacion 
entre aplicaciones compuestas y procesos de negocio. Te habilita para que 
facilmente se puedan ensamblar multiples tecnologías en una sola "SOA Composite
Application".
SOA Suite provee el siguiente set de capacidades de integracion:
* Messaging
* Service Discovery
* Orchestration
* Web services management and security
* Business Rules
* Human interation
* Events framework
* Business activity monitoring

Estandars usados por SOA Suite:
* SCA (Service Component Architecture)
* SDO (Service Data Objects)
* BPEL (Business Process Execution Language): Estandar para orquestacion y de 
ejecución de procesos de negocio, integrando servicios. (Soporta versiones 1.1 y 2.0)
* XSLT (XSL Transformations)
* XQuery
* JCA (Java Connector Architecture): Provee una solución java al problema de
conectividad entre la mayoria de servidores de aplicaciones en un EIS.
* JMS (Java Messaging Service): Provee mensajeria estandar que permite
a los componentes basados en Java2, JavaEE acceder a logica de negocio
distribuida entre sistemas heterogeneos.
* WSDL
* SOAP
* REST
* JSON
* WADL

# Services Component Architecture 

Beneficios de usar SCA:
 * Bajo acoplamiento
 * Flexibilidad
 * Invocacion de servicios
 * Productividad
 * Facil de mantener y debbug

SOA composite es un ensamblado de servicios, componente de servicio desplegados
en una sola aplicaciones. 
Los detalles de la composicion estan en el fichero composite.xml

# Servivces Components
 * BPEL: Provee procesos de orquestacion y almacenamiento de procesos sincronos
         o asincronos. Diseñas un proceso de negocio que integra una serie de 
         actividades de negocio y servicios en un flujo end-to-end.
 * Business Rules:  Te ayuda a diseñar una decision de negocio basado en reglas
 * Human Tasks: Provee un flujo de trabajo que modela y describe las tareas para
                usuarios o grupos de usuarios y presentarlos como parte del flujo de proceso.
 * Mediators: Ruteo de eventos(mensajes) entre diferentes componentes.
 * Spring : Habilita la integracion de interfaces JAVA 

# Binding Components
 * Services: Provee un punto de entrada a la aplicacion SOA Composite del mundo exterior.
             El archivo WSDL informa de las capacidades de la aplicacion para que
             pueda ser consumida. El binding connectivity describe los protocolos
             que pueden comunicarse con el servicios (SOAP/HTTP, JCA Adapter)
 * References: Habilita los mensajes para ser enviados desde la aplicacion SOA
               Composite hacia servicios externos.
 * Binding Components: 
    * Web service (SOAP/HTTP)
    * JCA Adapters 
    * Oracle B2B: Usado para el browsing de metadata en el MDS Repository.
    * Oracle Healthcare: Usado para enviar y recibir mensajes de un healthcare system.
    * ADF-BC Service: Usado para conectar Oracle Application Development Framework.
    * Oracle E-Business Suite: Usado para integrar Oracle E-Business Suite
    * BAM 11g adapter: Usado para integrar Java EE applications con Oracle BAM
                       Solo conecta un Oracle BAM 11g server.
    * EJB Service: Usado para integrar SDO parameters o interfaces Java con EJB.
    * Direct binding service: Usado para invocar aplicaciones SOA composite e 
                              intercambiar mensajes sobre RMI, invocar por ejemplo
                              flujos OSB (inbound direction) o alguna otra aplicacion
                              SOA Composite(outbound direction).
    * HTTP Binding
    * Rest Service
    * Oracle Managed File Transfer: Usado para transferir archivod entre 
                                    muchos puntos finales (FTP, SFTP, directorios,
                                    SOAP, OSB, SOA Suite, etc).
    * Cloud Adapters: Habilita la oportunidad de enviar y recivir mensajes de
                      un cloud server.
# Comportamiento en tiempo de ejecucion de un SOA Composite
 * Binding components: Service o Reference, reciben el mensaje y lo colocan en 
                       el Service Infraestructure.
 * Service Infraestructure: Recibe el mensaje de el binding y lo coloca en 
                            el Service engine correspondiente.
 * Service Engine: Almacena la logica de negocio o procesa las reglas del service composite,
                   Recibe el mensaje de el service infraestructure y lo envia a 
                   una aplicacion externa, el mensaje de respuesta lo coloca en 
                   el service infraestructura despues de terminar el proceso.
 * UDDI y MDS: MDS almacena la descripcion de los servicios disponibles, 
               UDDI habilita el discovery y el binding dinamico en tiempo de ejecucion.
 * SOA archive Composite: SAR que es la unidad de despliegue.












































































































