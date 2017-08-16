#Introduction to Interaction Patterns in a BPEL Process

#One Way Messages

 * El cliente envia un mensaje al servicio y el servicio no esta obligado a responder
 * El cliente envia el mensaje y no espera respuesta, pero continua ejecutandose inmediatamente.
 * Un cliente necesita un "invoke activity" y no espera respuesta.
 * Un proceso BPEL en el lado del servicio necesita un "receive activity", sin emitir una respuesta

#Synchronous Interactions
 * El cliente envia un "request" al servicio y recibe "inmediatamente" una respuesta.
 * Un proceso BPEL en el lado del cliente necesita un "invoke activity"
 * Un proceso BPEL en el lado del servicio necesita un "receive activity", un "reply activity"
   y de ser el caso un "error message(fault)"

# Asynchronous Interactions
 * El cliente envia un "request" a un servicio y espera(sin timeout) hasta que el servicio responda
 * El proceso BPEl en el lado del cliente necesita un "invoke activity" para enviar el "request"
   y un "receive activity" para recibir la respuesta.
 * El proceso BPEL en el lado del servidor necesita un "receive activity" para recibir el mensaje
   y un "invoke activity" para enviar la respuesta o el mensaje de error.
 - Tip: A diferencia de la interaccion sincrona que usa un "reply activity", la interaccion asincrona envia la respuesta
        usando un "invoke activity".
# Asynchronous Interactions with Timeout
 * El cliente envia un "request"  a un servicio y espera a recibir un reply o hasta que cumpla un timeout,
   lo que suceda primero.
 * El proceso BPEL en el lado del cliente necesita un "invoke activity" para enviar el "request"
   ademas un "pick activity" con dos ramas; rama "onMessage" y la rama "onAlarm".
   Si la respuesta pasa el limite de tiempo(timeout) el mensaje sera dirigido a una dead letter queue.
 * El proceso BPEL en el lado del servidor necesita un "receive activity" para recibir el mensaje
   y un "invoke activity" para enviar la respuesta o el mensaje de error.
#Introduction to Asynchronous Interactions with Notification Timer
 * El proceso BPEL en el lado del cliente es notificado que el tiempo expiró,
   pero aun asi espera la respuesta del lado del servidor.
   Generalmente se usa un "invoke activity" y un "receive activity", además de
   configurar en el scope la accion "onAlarm"
 * El proceso BPEL en el lado del servidor necesita un "receive activity" para recibir el mensaje
   y un "invoke activity" para enviar la respuesta.

#Introduction to One Request, Multiple Responses
 * Un cliente envia un unico "request" y el servidor responde con multiples "response"
 * El proceso BPEL del lado del cliente necesita un "invoke activity" y multiples
   "receive activities", una por cada "response".
 * El proceso BPEL del lado del servidor, necesita un "receive activity" y multiples
   "invoke activities".
#Introduction to One Request, One of Two Possible Responses
 * El proceso BPEL del lado del cliente, usa un "invoke activity", ademas 
   un "pick activity" con dos ramas "onMessage", de acuerdo a la respuesta del proveedor.
 * El proceso BPEL del lado del servidor, usa un "receive activity" y un "switch activity"(BPEL 1.1)
   y un "if activity" (BPEL 2.0). en cada uno de estos, de acuerdo a la logica de negocio
   se usa un "invoke activity".
#Introduction to One Request, a Mandatory Reponse, and an Optional Response
 * El proceso BPEL del lado del cliente necesita un scope que contenga un "invoke activity"
   y un "receive activity" para aceptar la respuesta obligatoria.
   El "onMessage handler" acepta un mensaje opcional y las instrucciones de que debeia hacer.
   Si el proceso en el lado del cliente recibe la respuesta obligatoria, continua su proceso
   sin esperar al mensaje opcional.
 * El proceso en el lado del servidor necesitara un "receive activity"y un "invoke activity"
   para enviar la respuesta obligatoria.y en el "onAlarm" para enviar el mensaje opcional.

#Introduction to Partial Processing
 * En un proceso parcial, el cliente envia una solicitud y recibe una respuesta inmediata
   pero el servidor sigue realizando un proceso que constantemente enviara mensajes al cliente.
 * El proceso BPEL en el lado del cliente necesita un "invoke activity" para cada request 
   y un "receive activity" por cada respuesta .
 * El proceso BPEL en el lado del servidor, necesita un "receive activity" para cada solicitud
   y un "invoke activity" para cada respuesta.

#Introduction to Multiple Application Interactions

 * Este patron A-to-B-to-C-to-A  de transaccion necesita un manejador de transacciones multples al mismo tiempo.
 * Existe un mecanismo requerido para hacer siguimiento a cada mensaje.
 * La coordinacion puede ser manejada usando WS-Addressing.


























































