# Developing SOA Composite Applications

- Tip: El nombre del proyecto determina su unicidad (Si un proyecto con nombre XXX
       es creado con el mismo nombre en otra aplicacion, será reemplazado)
# Templates

 * Empty Composite: Crea una aplicacion SOA Composite vacia.
 * Composite With BPEL Process: Automaticamente abre el "Create BPEL Process", que 
                                guía para la creacion de un proceso inicial de BPEL.
 * Composite With Mediator: Automaticamente abre el "Create mediator", que guia 
                            para la creacion de un componente Oracle Mediator.
 * Composite With Human Task: Abre dialogo para la creacion de un Human Task
 * Composite With Subprocess: Crea un SOA Composite con un subproceso, un subproceso
                              es un fragmento de BPEL que puede ser reusado.
 * Composite With Business Rule: Abbre dialogo para la creacion de un Business Rule.
 * Composite With Spring: Crea un dialogo de Spring que guia para el contexto spring,
                          reemplazando el WSDL por interfaces Java.

# Componentes de un proyecto SOA 
 * Service Component Directory: Muestra un directorio para cada componente que se agregue.
                                Un BPEL, Mediator, HumanTask, oracle/rules(business rules)
 * Events: Muestra los archivos business events (.edn)
 * Schemas: Muestra los archivos BPEL process schema (.xsd)
 * testsuites: Muestra los archivos test suite
 * Transformations: Muestra los archivos de transformacion Xquery y XSLT
 * WSDLs: Muestra los archivos WSDL
 * composite name: archivo que es automaticamente creado cuando creas un proyecto SOA.
                   Describe el "composite" donde se ensamblan, servicios, componentes, 
                   referencias y wires.
# Composite File
 * La parte izquierda(Exposed Services): Aqui se colocan los services(como WS, REST, JCA) que proveen
                                         un punto de entrada para la aplicacion SOA.
 * La parte derecha(External References): Aqui se colocan los references para enviar 
                                          mensajes a servicios externos,
                                          (web services, JCA Adapters), desde la aplicacion SOA.
 * Parte central(Components): Components(BPEL, Business Rules, Human Tasks, Mediators, spring components) y
                              Technology( JCA Adapters(FTP, database, JMS, MQ, etc) third party adapter, cloud
                              adapter, etc)
# Service Editors:
 * SOAP: Crea un dialogo para crear un servicio web de invocacion
 * Adapters: Wizard para la creacion de componentes para la integracion con
             FTP server, JMS, IBM MQ, BAM, LDAP, Coherence cache, Sockets, SAP
             Oracle E-Business
 * ADF-BC
 * B2B
 * Healthcare
 * EJB
 * HTTP
 * Direct
 * REST
 * MFT

- Tip: Tener cuidado de que cada WSDL tiene que tener un diferente namespace.
- Tip: Al eliminar un "service" se eliminan todas sus referencias y todos sus enlaces
- Tip: Cuando un componente es eliminado, tambien se elimina su WSDL asociado, en el 
       caso de que otro componente lo use (el wsdl), no se elimina.
- Tip: Cuando un WSDL se cambia de ubicacion; recordar cambiar las referencias de los siguientes lugares
       User interface location(JDeveloper)
       Import: durante el despliegue
       La ubicacion en las referencias definidas (Usado durante tiempo de ejecucion)
# Wires

- Tip: Oracle Mediator solo puede ser enlazado por un "servicio inbound", por lo tanto 
       rechazara los intentos de crear un segundo servicio.
- Tip: No se puede enlazar "external references" a un business rule, ya que no soporta referencias.
- Tip: No se pueden conectar servicios y composites que tienen diferentes interfaces, 
       Por ejemplo, no puedes conectar servicios configurados con un WSDL sincrono 
       con un proceso BPEL asincrono.
- Tip: Un "service" y un "reference" debe hacer match, significa que la interface
       y su callback deben ser el mismo. Si dos servicios que tienen diferentes
       interfaces quieren comunicarse, se podria usar un Oracle Mediator para mejroar
       la transformacion entre interfaces.
- Tip: No se puede renombrar Human Tasks, subprocess o business rules.
- Tip: No se pueden mover componentes o bindings a otra carpeta























































































































































































































