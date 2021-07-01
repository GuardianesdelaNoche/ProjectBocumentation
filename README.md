#Web Development Bootcamp X Final Project
*by Guardianes de la noche*

## Objetivo de este proyecto

Desarrollar un portal web donde gente con ganas de organizar eventos al aire libre o en sitios cubiertos, como sesiones de Taichi, pilates, zumba, excursiones por la montaña, en definitiva eventos dirigidos, tengan la oportunidad de poder ofecerlos a través de nuestro portal, de una forma fácil, dinámica y que tengan alta difusión para poder llegar a diferentes públicos. Y por otro lado, usuarios que quieran apuntarse a estas clases dirigidas o eventos, que tengan un sitio dónde poder encontrarlos, apuntarse o suscribirse a ellos de forma muy fácil.
En esta primera fase no habrá pasarela de pago, por lo que si algún evento no es gratuido, deberá abonarse el importe al organizador el dia del evento.

## Nombres a proponer en nuestro proyecto y dominio
actividades-dirigidas.com  
actividadesdirigidas.com  
espacio-salud.com  
espaciobienestar.com  
.....

## Consideraciones generales
1. La plataforma estará preparada para trabajar en multi idioma.
2. Las tecnológias principales a utilizar en nuestro proyecto son:
	* React Redux para desarrollo web (front end).
	* NodeJS para la parte del API (back end).
	* MongoDB como base de datos.

3. Sistemas y apoyo:
	* AWS como plataforma para el despliegue de nuestras aplicaciones.
	* Ubuntu como sistema operativo.
	* Trello para nuestra organización. Tareas y sprints
	* GitHub como repositorio.  
	
## Componentes principales de la plataforma
Nuestra plataforma cuenta con tres componentes principales:

1. **Zona pública:** zona que podremos acceder sin estar autenticados y donde podremos solicitar el alta como usuario.
2. **Zona privada:** La zona privada sólo será accesible por usuarios que previamente hayan sido dados de alta y admitidos en el caso de publicadores. Dependiendo de su rol, los usuarios podrán publicar eventos, modificarlos, darlos de baja o bien suscribirse a otros anuncios de eventos.
3. **API REST:** Queremos ofrecer un API REST que dará servicio a las peticiones de nuestro portal web y para que en un futuro se puedan conectar clientes u otras aplicaciones (móviles, de escritorio, etc.) a nuestros servicios.

## Roles definidos
Tras el análisis de nuestro proyecto, detectamos los siguientes roles en nuestra aplicación: 
   
1. Usuario anónimo: usuario que no necesita ningún tipo de autenticación y que podrá acceder a los siguientes servicios:   
	* Registrarse para darse de alta como usuario nuevo.  
	* Búsqueda y visualización de eventos. Restringido a consultas.
2. Usuario Super Administrador:
	* Podrá dar de alta a otros super administradores.
	* Podrá aceptar a otros administradores-publicadores.
	* Podrá dar de alta, modificar, eliminar y vetar a administrador-publicador.
	* Podrá vetar eventos publicados.
3. Usuario Administrador-publicador:
	* Este usuario podrá publicar nuevos eventos y administrar los eventos que haya publicado el mismo.
	* También podrá suscribirse a cualquier evento publicado.
	* Podrá acceder y modificar su perfil.
4. Usuario consumidor de eventos:
	* Podrá suscribirse a cualquier evento publicado.
	* Podrá acceder y modificar su perfil.
	
## Funcionalidades e historias de usuario
Detallamos las funcionalidades de nuestra plataforma, agrupadas por areas.

### Zona pública

#### Registro de usuarios
* Como usuario anónimo desde la zona pública, quiero poder darme de alta en el sistema para poder así autenticarme y poder realizar funciones como miembro de la plataforma indicando los siguientes datos:
	- Nombre y un apellido mínimo.
	- Nickname.
	- e-mail válido.
	- Dirección.
	- Código postal.
	- Población.
	- Teléfono de contacto.
	- Año de nacimiento.
	- Contraseña segura (ver restricciones)
	- Repetir contraseña para verificar que es correcta.
	- Foto o avatar (campo NO obligatorio).
	- Sólo consultar o consultar y publicar.
	- Acepta recibir correos de nuevos eventos donde se haya suscrito(true-false)
	

* Restricciones/criterios de aceptación
	- Para los usuarios de tipo Administrador-publicador
		* Todos los campos, exceptuando la foto, son obligatorios.
		* El usuario podrá acceder a la parte privada para suscribirse a eventos de forma inmediata.
		* El usuario quedará a la espera de su aceptación por parte de un super administrador para poder ofrecer o subir anuncios de eventos.
	- No se aceptan nicknames, cuentas de e-mail duplicadas.
	- Las contraseñas deberán tener un mínimo de 8 posiciones con un máximo de 15 y deberán contener un minimo de 1 letra máyuscula y 1 número.


#### Recuperación de contraseña
* Como usuario registrado quiero poder recuperar mi contraseña en caso de necesidad.

* Restricciones/Criterios de aceptación
	- Para recuperar la contraseña, el usuario deberá indicar la dirección de e-mail asociada a su cuenta de usuario.
	- Cuando el usuario indique el e-mail correcto, deberá recibir un correo con un enlace que permita reestablecer su nueva contraseña.


#### Login de usuario
* Como usuario anónimo quiero poder hacer login en la plataforma para acceder a la zona privada y así poder acceder a todas las funcionalidades que tenga habilitadas para mi perfil.  

* Restricciones/Criterios de aceptación
	- Sólo podrán autenticarse usuarios registrados en nuestra plataforma.
	- Para autenticarse deberán indicar su nombre de usuario y contraseña.
	- Una vez autenticados, guardaremos la fecha y hora UTC actual en el perfil de usuario.


#### Ver Listado de los últimos eventos
* Como usuario anónimo quiero poder acceder a un listado de los últimos eventos publicados de manera rápida.

* Restricciones/Criterios de aceptación.
	- Se deben mostrar los últimos eventos publicados por orden cronológico, siendo el primero el más reciente y el último el más antiguo.
	- Debemos utilizar la paginación para enseñar una cantidad determinada de eventos en cada consulta.
	- En la paginación poder acceder directamente a la primera y última página. 
	- El usuario podrá elegir cuantos eventos quiere ver en cada paginación (10,20,50,100).
	- Sólo se mostrarán los eventos que todavía no se han iniciado.
	- Cada evento tendrá una fecha-hora de inicio y fecha-hora fin.
	- Cada evento deberá mostrar: nombre, imágen, descripción, precio o gratuito, plazas disponibles, dia del evento, duración y autor.
	

#### Busqueda y filtro de eventos
* Como usuario anónimo quiero poder buscar eventos utilizando un buscador que me permita encontrar los eventos que a mi me interesan de forma fácil y rápida.

* Restricciones/Criterios de aceptación.
	- El usuario podrá buscar por los siguientes criterios:
		* Nombre del evento.
		* Por cercanía a un código postal (Radio en km.).
		* Tipo de evento (Pendiente de clasificación).
		* Nivel de dificultad.
		* Edad recomendada (Marcar criterios de edad + todas).
		* Fecha del evento (inicio) o rango de fechas.
		* Promotor u organizador.
		* Aire libre o no
		* Ordenar por antiguedad o por inicio del evento.
	- Sólo se mostrarán eventos no iniciados.
	- Criterio de odenación descendente por fecha según filtro punto anterior.
	- Debemos utilizar la paginación para enseñar una cantidad determinada de eventos en cada consulta.
	- En la paginación poder acceder directamente a la primera y última página. 
	- El usuario podrá elegir cuantos eventos quiere ver en cada paginación (10,20,50,100).
	- Sólo se mostrarán los eventos que todavía no se han iniciado.
	- Cada evento tendrá una fecha-hora de inicio y fecha-hora fin.
	- Cada evento deberá mostrar: nombre, imágen, descripción, precio o gratuito, plazas disponibles, fecha-hora del evento, duración y autor.


#### Ver detalle de un evento
* Como usuario anónimo quiero poder acceder al detalle de un evento desde algún listado de eventos para poder leer todo su contenido.

* Restricciones/Criterios de aceptación.
	- Cada evento deberá tener una URL única.
	- La URL de un evento deberá ser SEO-Friendly: deberá de aparecer de alguna manera el nombre del evento.
	- Cada evento deberá mostrar:
		* Nombre
		* Imágen
		* Descripción
		* Precio o gratuito
		* Plazas disponibles
		* Fecha-hora inicio del evento
		* Duración
		* Organizador
		* Clasificación (tipo evento)
		* Aire libre o no
		* Valoración general de los usuarios al autor 
		* Localización del evento (Dirección, población, coordenadas)
		* Pintar posición en mapa (Si es posible).
		* ...

#### Compartir un evento en redes sociales
* Como usuario quiero poder compartir un evento en redes sociales y así hacer participe a mi entorno eventos que puedan ser interesantes.

* Restricciones/Criterios de aceptación.
	- Se deberá poder compartir, como mínimo, en Twitter o Facebook.

#### Ver eventos de un miembro
* Como usuario anónimo quiero poder acceder a un listado de los últimos eventos publicados por un miembro de la plataforma específico cuando acceda a la url de su perfil.

* Restricciones/Criterios de aceptación
	- Las URLs de los miembros de la plataforma deberán ser:
		* /<nombre_de_usuario_del_miembro>/
	- Se deben mostrar los últimos eventos publicados por dicho miembro por orden cronológico siendo el primero más reciente y el último el más antiguo.
	- Los eventos mostrados se paginarán con el mismo critero que se ha descrito en puntos anteriores.
	- Cada evento deberá mostrar: nombre, imágen, descripción, precio o gratuito, plazas disponibles, dia del evento, duración y autor.

	
### Funcionalidades de la zona privada.

#### Baja de usuario
* Como miembro de la plataforma, quiero poder dar de baja mi cuenta desde la zona privada para dejar de ser miembro de la plataforma.

* Restricciones/Criterios de aceptación.
	- Se deberá eliminar toda la información relacionada con el usuario que se da de baja.


#### Actualización de datos de usuario
* Como miembro de la plataforma, quiero poder actualizar mis datos desde la zona privada incluso poder modificar mi contraseña.

* Restricciones/Criterios de aceptación.
	- Un usuario sólo podrá modificar sus datos si está autenticado.
	- El nickname o el e-mail nunca se admitirán duplicados.


#### Logout de usuario
* Como miembro de la plataforma quiero poder cerrar la sesión de mi usuario y evitar que nadie pueda utilizarlo en mi ordenador.

* Restricciones/Criterios de aceptación.
	- Sólo se podrá cerrar la sesión de usuario si este está autenticado.


#### Ver listado de todos mis eventos
* Como miembro, quiero poder acceder al listado de todos mis eventos publicados, para poder editarlos o eliminarlos.

* Restricciones/Criterios de aceptación.
	- Un miembro sólo podrá modificar o borrar los eventos creados por él.
	- Será necesario estar autenticado para acceder al listado de eventos propios.
	- Como mejora adicional, se deberían poder visualizar la relación de usuarios que se han apuntado al evento.


#### Ver listado de todos los eventos a los que me he apuntado
* Como miembro, quiero poder acceder al listado de todos mis eventos a los que me he apuntado.

* Restricciones/Criterios de aceptación.
	- Será necesario estar autenticado para acceder al listado de eventos suscritos.
	- Para visualizarlos, se utilizará el mismo criterio que en los otros listados de eventos.


#### Crear un evento
* Como miembro de la plataforma quiero poder crear a través de un formulario, sencillo y fácil de utilizar, un nuevo evento

* Restricciones/Criterios de aceptación.
	- Sólo los usuarios miembros podrán crear eventos.
	- Un evento estará formado por:
		* Nombre
		* Imágen
		* Descripción
		* Precio o gratuito
		* Plazas que se ofrecen
		* Fecha-hora inicio del evento
		* Fecha-hora inicio del evento
		* Organizador
		* Clasificación (tipo evento)Tags donde se asocia
		* Aire libre o recinto cerrado 
		* Localización del evento (Dirección, población, coordenadas)
	- Cuando se cree el evento, deberá quedar reflejado el autor que lo ha creado


#### Editar un evento
* Como miembro de la plataforma quiero poder acceder a la edición de un evento a través del listado de mis eventos para poder así modificarlo.

* Restricciones/Criterios de aceptación.
	- Sólo el miembro propietario del evento podrá editarlo.
	- Si se llegara a incorporar el super-usuario-administrador, este también podría.
	- Si hay modificaciones en eventos con suscripciones o incluidos como favoritos, se deberá comunicar a los afectados a través de e-mail.


#### Borrar un evento
* Como miembro de la plataforma quiero poder eliminar un evento.

* Restricciones/Criterios de aceptación.
	- Sólo el miembro propietario del evento podrá eliminar el evento.
	- Si llegara a incorporarse el super-usuario-administrador, este también podría.
	- La eliminación del evento se deberá confirmar para evitar errores o acciones involuntarias.
	- Si hay borrado de eventos con suscripciones o incluidos como favoritos, se deberá comunicar a los afectados a través de e-mail.



#### Cancelar un evento
* Como miembro de la plataforma, quiero poder cancelar un evento por cualquier motivo.

* Restricciones/Criterios de aceptación.
	- Sólo el miembro propietario del evento podrá cancelar el evento.
	- El miembro propietario del evento podrá indicar el motivo de la cancelación.
	- Si hay cancelación de eventos con suscripciones o incluidos como favoritos, se deberá comunicar a los afectados a través de e-mail.


#### Suscribirse o darse de baja a un evento
* Como miembro registrado, quiero poder darme de alta a cualquier evento publicado o bien darme de baja en el evento suscrito.

* Restricciones/Criterios de aceptación.
	- Sólo usuarios registrados podrán darse de alta en eventos.
	- Para darse de baja en un evento, debo ser el usuario que se suscribió o bien el propietario del evento.
	- Si con nuestra suscripción al evento completamos todas las plazas disponibles, deberemos notificar a los usuarios registrados que la tenían como favorita, que ya no quedan plazas en su evento favorito.


#### Marcar o desmarcarcar un evento como completo
* Como miembro registrado o anónimo no quiero visualizar anuncios que no tengan plazas disponibles.

* Restricciones/Criterios de aceptación.
	- Afecta a todos los usuarios.
	- Los usuarios suscritos al evento, lo podrán visualizar en "Ver listado de todos mis eventos" y deberán tener la opción de darse de baja del evento.


#### Chatear entre promotor y consumidor del evento
* Como miembro de la plataforma, quiero poder chatear con otro miembro en relación a un evento para poder resolver dudas que puedan surgir.

* Restricciones/Criterios de aceptación.
* Sólo miembros de la plataforma podrán conversar entre sí (los usuarios anónimos no pueden chatear)
* Las conversaciones se deberán clasificar por evento, no por miembros que participan en ella (dos miembros pueden tener varias conversaciones diferentes, una por cada evento)


#### Ver eventos favoritos
* Como miembro de la plataforma, quiero poder acceder a mis eventos guardados como favoritos para acceder directamente a ellos.

* Restricciones/Criterios de aceptación.
	- Un miembro de la plataforma sólo debe ver los eventos que él ha guardado como favorito.


#### Guardar o eliminar evento como favorito
* Como miembro de la plataforma, quiero poder guardar eventos como favoritos o bien borrar suscripciones ya realizadas.

* Restricciones/Criterios de aceptación.
	- Un miembro sólo podrá eliminar sus anuncios guardados como favoritos.
	- Sólo usuarios miembros podrán guardar anuncios como favoritos


#### Recibir una notificación cuando un evento favorito se marque como completo o cancelado
* Como miembro de la plataforma quiero recibir notificaciones cuendo un evento favorito ya no esté disponible, por motivos de cancelación o compeltado en max. de personas admitidas.

* Restricciones/Criterios de aceptación.
 - Sólo usuarios miembros de la plataforma.


#### Recibir una notificación cuando un evento favorito esté a punto de agotar su capacidad
* Como miembro de la plataforma quiero recibir una notificación cuando a un evento le queden muy pocas plazas disponibles (una o dos).

* Restricciones/Criterios de aceptación.
	- Sólo usuarios miembros de la plataforma.
	- Si el miembro está conectado, deberá mostrarse en tiempo real la notificación
	- Si el miembro no está conectado, se deberá enviar la notificación por e-mail
	- Sería interesante que tanto la notificación como el e-mail permitiera realizar algunas acciones como: desmarcar evento como favorito o ver detalle del evento.


#### Recibir una notificación de nuevos mensajes de chats sin leer
* Como miembro de la plataforma, quiero recibir notificaciones de nuevos mensajes de chat sin leer para así estar al tanto de las conversaciones sobre los eventos en los que estoy interesado.

* Restricciones/Criterios de aceptación.
	- Si el miembro está conectado, deberá mostrarse en tiempo real la notificación (sólo se deberá mostrar la notificación si el usuario no está visualizando el chat en ese momento.)
	- Si el miembro no está conectado, se deberá enviar la notificación por e-mail
	- Sería interesante que tanto la notificación como el e-mail permitiera abrir directamente el chat.


#### Recibir un email de eventos de interés
* Como miembro de la plataforma, quiero recibir e-mail de eventos que encajen con alguno de los eventos de suscripción o búsqueda que tengo para así encontrar más fácilmente un suscriptor o promotor.

* Restricciones/Criterios de aceptación.
	- El e-mail deberá incluir un enlace al detalle del anuncio.

### Conclusiones finales
Creemos que es un proyeco bastante ambicioso por el tiempo del que disponemos.
Este documento nos tiene que servir de guía base para poder definir las tareas e historias a desarrollar y según vayamos avanzando en el proyecto, incorporar más grado de funcionalidad.
En una primera fase daríamos una vuelta al proyecto, desarrollando lo más básico, en una segunda ronda ya aumentaríamos el grado de funcionalidad y si hay una tercera, terminamos el proyecto tal y como está detallado en este documento.
En primera ronda, se desarrollaría la máxima funcionalidad posible del back-end ya que es el pilar principal que nos permitirá crecer en funcionalidad en el front-end.


