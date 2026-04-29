# CIB302
pagina web con auth0 y simulación de carrito de compra.

1. Flujo de autenticación con Auth0
La aplicación SportyStyle implementa autenticación de usuarios utilizando Auth0, una plataforma externa que permite gestionar el inicio de sesión de forma segura sin necesidad de desarrollar un sistema propio.
El flujo de autenticación funciona de la siguiente manera:
1.	El usuario hace clic en el botón "Iniciar Sesión" dentro de la aplicación. 
2.	Es redirigido automáticamente a la página de autenticación de Auth0. 
3.	El usuario ingresa sus credenciales (correo y contraseña). 
4.	Auth0 valida la información y, si es correcta, redirige nuevamente al usuario a la aplicación. 
5.	Una vez autenticado, el sistema obtiene la información básica del usuario (como su nombre) mediante el SDK de Auth0. 
6.	Se muestra un mensaje de bienvenida personalizado en la interfaz. 
Es importante destacar que:
•	No se manejan tokens manualmente. 
•	Auth0 gestiona internamente la seguridad, validación y almacenamiento de sesión. 
•	Esto permite una implementación más segura y simplificada. 
2. Proceso de selección de productos y uso de Session Storage
La tienda virtual permite a los usuarios seleccionar productos y agregarlos a un carrito de compras dinámico.
Selección de productos
Cada producto disponible en la tienda incluye:
•	Imagen 
•	Nombre 
•	Descripción 
•	Precio 
•	Botón "Agregar al carrito" 
Cuando el usuario hace clic en este botón:
1.	El producto se agrega al carrito. 
2.	Si el producto ya existe, se incrementa su cantidad. 
3.	El carrito se actualiza automáticamente en pantalla. 

Uso de Session Storage
Para almacenar los productos seleccionados, se utiliza Session Storage, que permite guardar datos en el navegador mientras la sesión está activa.
Funcionamiento:
1.	Cada vez que se agrega un producto, el carrito se guarda en Session Storage en formato JSON. 
2.	Al recargar la página, los datos se recuperan automáticamente. 
3.	Esto permite mantener el carrito activo durante toda la navegación del usuario. 
Ventajas:
•	No requiere base de datos. 
•	Es rápido y eficiente. 
•	Los datos se eliminan automáticamente al cerrar la pestaña o navegador. 

3. Mantenimiento de la sesión activa
La aplicación mantiene la sesión activa utilizando dos mecanismos principales:
Auth0 (sesión de usuario)
•	Auth0 se encarga de mantener autenticado al usuario. 
•	Mientras la sesión no expire, el usuario permanece logueado. 
•	No es necesario reingresar credenciales durante la navegación. 
•	
•	
Session Storage (carrito de compras)
•	Los productos agregados al carrito se mantienen disponibles mientras la sesión del navegador esté activa. 
•	El carrito no se pierde al cambiar de página o recargar. 
Finalización o cierre de sesión
Cuando el usuario:
•	Hace clic en "Cerrar sesión", o 
•	Completa una compra, 
ocurre lo siguiente:
1.	Se elimina la sesión del usuario en Auth0. 
2.	Se limpia completamente el Session Storage. 
3.	El carrito vuelve a estar vacío. 
Conclusión
La aplicación SportyStyle logra simular una experiencia de compra completa mediante la integración de autenticación segura con Auth0 y la gestión de datos en Session Storage. Esto permite ofrecer una navegación fluida, mantener la sesión activa del usuario y garantizar una interacción simple y eficiente sin necesidad de backend complejo.
