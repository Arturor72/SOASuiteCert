# Getting Started with Oracle BPEL Process Manager

- Tip: No se puede usar la sintaxis de BPEL 1.1 y BPEL 2.0 en el mismo fichero .bpel
       Sin embargo si se puede usar proyectos BPEL 1.1 y BPEL 2.0 en la misma aplicacion SOA composite.
# Creacion de un flujo BPEL

* BPEL Specification: Se puede seleccionar la version de BPEL segun si especificación.
* Name: El nombre del proceso BPEL llegara a ser tambien el nombre del WSDL en la ventana de aplicacion.
        No se permiten numeros al inicio del nombre no puede incluir guión, no se permiten 
        crear flujos con el mismo nombre a pesar de tener mayusculas y minusculas diferentes,
        esto debido a que cuando se use Oracle BAM, esta aplicacion transforma todos los nombres 
        a mayusculas.
* Namespace: Se puede cambiar el namespace que viene por defecto.
* Directory: Se puede cambiar el directorio, siempre en cuando se encuentre debajo del directoria SOA.
* Template: Pueden ser:
  * Asynchronous BPEL: Crea un proceso asincrono con la actividad "receive" que inicializa el BPEL
                       y una actividad "invoke" con una llamada asincrona al cliente.
  * Synchronous BPEL: Crea un proceso sincrono con la actividad "receive" que inicializa el BPEL
                      y una actividad "reply" que retorna los resultados.
  * One Way BPEL: Crea un proceso con una llamada one-way.
  * Base on a WSDL: Crea un BPEL con una interface definida por un WSDL que ya existe. 
                    Se debe especificar la URL del WSDL.
  * Subscribe to Events: Crear un BPEL que puede estar suscrito a un "Business Event".
                         El dialogo desplegara una tabla de eventos. Seleccionar el
                         evento al que  se requiere suscribi.
  * Service Name: Colocar el nombre del servicio que el BPEL esta exponiendo,
                  Cuando abres las actividades (invoke, receive, OnMessage o reply) 
                  el nombre del servicio aparecera por defecto, es el mismo 
                  nombre que el Partner Link.
  * Expose as a SOAP Service: Crea un PEL que es automaticamente conectado a un 
                              inbound SOAP web service.
  * Delivery: Si seleccionaste (Async, One Way, Subscribe): Conjunto de politicas de persistencia
                               en la capa de entrega.
                               - Asyn.persist: Los mensajes son persistidos en una BD
                                               con esta configuracion, existe un pequeño impacto de performance
                                               hacia la base de datos. 
                               - Async.cache: Los mensajes de almacenan en memoria cache.Es mucho mas rapido en performance,
                                              pero debido a que los mensajes se encolan en "scheduled queue" si el servidor
                                              falla los mensajes se perderan. Ademas si es que existe una gran diferencia 
                                              entre los mensajes que entran y los que se entregan podría ocurrir un error de
                                              sobrecarga de memoria. Usarlo de acuerdo al caso de uso.
                               - Sync: Invocacion directa en el mismo hilo. El flujo BPEL es invocado de manera sincrona,
                                       En algunos casos puede mejorar la performance de base de datos.
  * Transactions: Si es un flujo sincrono se habilita, permite especificar un valor para la propiedad
                  de transacción para el despliegue.
                  * Required: Si existe una transaccion entonces la nueva transaccion se une o si no 
                              existe una transaccion lo crea.
                              Coloca el Delivery list value a sync
                  * RequiredNew: Una nueva transaccion es creada y si existe una transaccion la suspende.
                                 Coloca el Delivery list value a sync
                  * NoSupported: Habilita a los procesos de negocio a ejecutar sin transaccion.
                  (No aplipa para procesos intermedios, en este caso otro hilo con otra transaccion es usado
                  para el proceso del mensaje)
   * Input: Acepta un default esquema XSD o puedes selecionar uno.
   * Output: Acepta un default esquema XSD o puedes selecionar uno.

# Activities

* Assign: Manipular data, copiando contenido de una variable a otra.
* Invoke: Invoca a un servicio (identificado por su partner link) y especifica
          una operacion que el servicio realizará.
* Receive: Espera un "callback" con un mensaje response de la llamada a un servicio asincrono.
           Tambien es usado cuando un proceso empieza asincronamente a travez de un partner link.

# Partner Links 
 * Un partner link te habilita para que puedas definir servicios externos con los
   cuales un proceso BPEL interactuará.
 * Puedes definir partner links como services o references (JCA adapter, etc)
 * Caracteriza la relacion convencional entre dos servicios, definiendo roles de 
   cada servicio.
   * Name: Un unico nombre proveeido para el partner link.
   * Process: Muestra el nombre del proceso BPEL
   * WSDL URL: El nombre y ubicacion del WSDL o Java interface que es seleccionado
               para el partner link.
   * Partner Link Type: El partner link definido en el WSDL.
   * Partner Role: Role realizado por el partner link
   * My Role: Role realizado por el proceso BPEL. Si es un proceos sincrono
              el proceso BPEL no tendra rol.

- Tip: cada vez que se crea un partner link, es prefirible hacerlo desde la vista del composite
       como service o reference























































































































