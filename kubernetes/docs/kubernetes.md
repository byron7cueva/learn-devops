# Kubernetes

* Es una plataorma de orquestación.
* Empezo en el 2016.
* Utiliza container runtime por debajo para poder orquestar todos sus servicios.
* Trabaja con una indentidad de orquestación que se llama POD.
* POD es la unidad de orquestación, este es un grupo de contenedores que pueden estar corriendo uno a lado del otro en el mismo host. Un POD vive en un nodo. Puede haber un Pod de un único contenedor o de múltiples contenedores.
*  Todos los contenedores que viven dentro de un Pod, comparten el mismo segmento de red (namespace de red). Es decir tienen la misma drección Ip y se ven unos a otros como un proceso que estan corriendo en el mismo sanbox.
* En kubernetes cuando se escala algo se escala el Pod, se crean copias de ese Pod para escalarlo. Son unidades que se reciclan.
* Es una herramienta que hace work look placement. Permite relacionar contenedores, hacer crecer nodos bajo demanda y correr contenedores o pod en nodos especificos y hacer que las aplicaciones se comuniquen entre si.
* Es una evolución de los proyectos de Google Borg & Omega.
* Kubernetes pertenece a la CNCF (Cloud Native Computing Foundation). CNCF Esta fundacion agrupa a algunos proyectos y tiene promotores de equipos y companias que apoyan el Open Source.
* Todos los cloud providers (GCP / AWS / Azure / DO) ofrecen servicios de managed k8s utilizando Docker como su container runtime.
* Es la plataforma más extensiva para orquestación de servicios e infraestructura.
* Corre varias réplicas y asegura que todas se encuentren funcionando.
* Provee un balanceador de carga (interno o externo) automáticamente para nuestros servicios.
* Definir diferentes mecanismos para hacer roll-outs de código. Permite definir estratégias de deployment.
* Políticas de scaling automáticas.
* Jobs batch
* Correr servicio con datos stateful
* Y muchas otras cosas (CRDs Custom resources definitions definir mis propios recursos, Service catalog saber que esta desplegado, RBAC Rol Base Access Control permite al orquestador dar políticas de roles)
* Se basa en el algoritmo de conseso de albitraje, esto permite tener varios master en el cluster y cuando uno de estos no responde, que otro tome el control.

## Arquitectura

![image-20201102113824599](./assets/arquitectura.png)

* Esta conformado por dos grandes partes:
  * Nodos master: Los que controlan el estado o cerebro de kubernetes.
  * Minions: Los nodes de trabajo.
* Se puede trabajar con kubernetes de dos manera:
  * API: Que expone la plataforma. Se lo puede hablar de una forma iperativo o modelo declarativo.
  * UI: Interfaz de usuario. Kubernetes Dashboard.
  * CLI: Línea de comandos. K CTL.

* Registro de imagenes: Los nodos se conectan al registro de la imagen.

![image-20201102115010005](./assets/arquitectura2.png)

Nodo Master

Control Plain o cerebro de kubernetes. Esta compuesto de:

* API Server: Es a lo que todo se conecta, como los agentes que viven en los nodos, cuando se ejecuta comandos en el K CTL o Kubernetes Dashboard. Al ser el cerebro del cluster es el que entiende que esta sucediendo, esto se pierde cuando un nodo cluster se cae. Es el unico que se conecta a etcd.
* Scheduler: Se encarga de cuando quiero crear algun tipo de trabajo ya sea un Pod o proceso. Este se encarga de decir tal Pod va a un nodo y este entiende cuanto recursos disponible tiene nuestro cluster. Asigna los contenedores y Pods a los nodos.
* Controler Manager: Es un proceso que esta en un ciclo de reconcilación constante. Lo que permite estar mirando constante mente al cluster e intentar que los servicios lleguen a ese estado deseado.
* etcd (key value store): Es una base de datos de alta disponibilidad, para lider election y cuando el nodo master se cae evitar que el cluster quede sin servicio.

Container Runtime

* Suele ser docker en la mayoria de los casos.
* Las ultimas versiones de kubernetes 1.14, ya vienen con Container De por default que es un subtrip down de lo que es el core de docker.

Kiubelet

* Es el agente de kubernetes, el que se conecta con el Control Plain y le pregunta que recursos debe correr. Es un proceso que esta corriendo constantemente y que se comunica con el API Server. Obtiene la información y se encarga de correr los contenedores o pods en el nodo. Actualiza el control plain con el estado de los contenedores.
* Corre los lines props, es la manera de decir si un Pod o contenedor funciona de la manera correcta.

Kiube-proxy

* Valancea el trafico que corre en el contenedor o servicios.
* Es el componente del cluster que se encarga cuando llega un paquete TCP/IP decide a donde tiene que ir, a que Pod y contenedor. 

## Modelo Declarativo e Imperativo

* Kubernetes hace énfasis en ser un sistema declarativo
* Declarativo: "Quiero una taza de té". A la hora de definir una tarea esta se define de manera que se le da un contexto y se le agrega una especificación le estoy diciendo como. Si por alguna razon se cae un nodo, entendiendo el contexto se puede observar y entender en donde se quedo o cuál fue ese error y volver y ver la diferencia entre el estado deseado y en donde me quede e intentar que se converga ha ese estado deseado. A traves de manifest file yaml declaro que quiero que suceda y a donde quiero que llegue el cluster.
* Imperativo: "Hervir agua, agregar hojas de té y servir en una taza". Esta compuesto sobre una serie de pasos que se los debe serguir a raja tabla de manera ciega sobre cual no se tiene un contexto. Si algún momento de todo ese proceso se interrumpe por algún motivo, tengo que comenzar desde principio para poderlo ejecutarlo. Es cuando utilizo el K CTRL o el dashboard y le digo que es lo que quiero que suceda, y si algo pasa pierdo el contexto de lo que estoy haciendo.
* Declarativo parece sencillo (siempre y cuando uno sepa cómo hacerlo).
* Todo en K8s se crea desde un spec que describe cuál es el estado deseado del sistema.
* Kubernetes constantemente converge con esa especificación.
* Hay una metodología llamada Git tops, lo que intenta es hacer que todas estas especificaciones las versione en un repositorio y luego el cluster tome estas de manera automática y empiece a converger.

## Modelo de Red

* Todo el cluster es una gran red del mismo segmento.
* Todos los nodos deben conectarse entre sí, sin NAT.
* Todos los pods deben conectarse entre sí, sin NAT.
* kube-proxy es el compenete para conectarnos a pods y contenedores (userland proxy / iptables)
* Los pods trabajan a capa 3 y los servicios a capa 4.
* Concepto de CNI (container networking interface). Arreglan reglas de Ip tables, las cuales permiten cambiar las reglas de enrutamiento.