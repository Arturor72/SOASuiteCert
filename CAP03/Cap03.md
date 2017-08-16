# Managing Shared Data with the Design-Time MDS Repository
- Tip: La configuracion de un MDS DesignTime se realiza en la seccion de
       recursos IDE Connections, a diferencia de un MDS normal, el MDS Design Time
       se almacena en una carpeta fisica en el host, aqui se pueden compartir recursos
       como WSDL, al ser compartidos por un proyecto, la referencia a estos recursos
       se hace a traves de el protocolo "oramds" por ejemplo  oramds:/apps.
       La configuracion de MDS Repository DesingTime se ve reflejada en el archivo
       de la aplicacion adf-config.xml
- Tip: Cerrar todas las ventanas antes de realizar un export o import de ficheros dentro del MDS
