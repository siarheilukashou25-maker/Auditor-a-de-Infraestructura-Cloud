# Auditoría de Infraestructura Cloud

En esta actividad hemos utilizado VS Code y la extensión XPath Notebook para generar un informe de consulta preciso, eficiente y sin afectar al rendimiento del servidor de producción.

**Misión 1: Mapeo de Seguridad (Navegación Absoluta/Relativa)**

El equipo de redes necesita auditar el firewall de Francia. Extrae una lista con todos los puertos de los servicios que se están ejecutando exclusivamente en el centro de datos de la ubicación "Paris".

    //centro_datos[@ubicacion='Paris']/servidor[@estado='activo']/software/servicios/servicio/@puerto  /string()

> "8888"

**Misión 2: Auditoría de Mantenimiento (Filtrado por Valores)**

Debemos planificar una ventana de actualización para sistemas operativos antiguos. Escribe una consulta que devuelva la versión del sistema operativo (SO) del servidor cuyo identificador (id) sea exactamente srv-db-01.

    //servidor[@id='srv-db-01']/software/so/@version  /string()
 
 

> "15"

**Misión 3: Inventario de Alta Capacidad (Predicados Matemáticos)**

El departamento de compras quiere saber qué infraestructura pesada tenemos. Recupera los nodos completos de los discos que tengan una capacidad igual o superior a 8 TB (independientemente de si son HDD o NVMe).

    //servidor/hardware/discos/disco[number(@capacidad_tb)  >=  8]

> [  
" /catalogo_cloud[1]/centro_datos[1]/servidor[2]/hardware[1]/discos[1]/disco[1]",  
" /catalogo_cloud[1]/centro_datos[2]/servidor[2]/hardware[1]/discos[1]/disco[1]"  
]

**Misión 4: Eficiencia Energética (Uso de Funciones o Índices)**

Para apagar temporalmente el hardware menos crítico, necesitamos identificar el primer servidor (nodo completo) que aparece registrado dentro de toda la infraestructura y que se encuentra actualmente en estado "apagado".

    (//servidor[@estado='apagado'])[1]

> " /catalogo_cloud[1]/centro_datos[2]/servidor[2]"

**Misión 5: Desafío del Auditor Senior (Navegación Inversa / Existencia)**

Necesitamos saber qué arquitectura de CPU se está utilizando en las máquinas de inteligencia artificial. Extrae el atributo arquitectura de la CPU que pertenezca al servidor que tiene instalada una GPU.

    //servidor[hardware/gpu]/hardware/cpu/@arquitectura  /string()

> "x86_64"


