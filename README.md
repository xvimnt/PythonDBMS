# Tytus DBMS Grupo # 08
### Cliente Desktop Linux
#### Universidad de San Carlos de Guatemala, Diciembre 2020
> Integrantes
> - Cinthya Andrea Palomo Galvez 201700670
> - Karla Julissa Ajtún Velásquez 201700565
> - Javier Alejandro Monterroso Lopez 201700831
> - Byron Antonio Orellana Alburez 201700733

# Manual de Usuario
![b9c88682-9c9c-4b84-9ba3-38f841784a9a](https://user-images.githubusercontent.com/14981793/102703787-fae75b00-4238-11eb-9b00-22158d07075b.jpg)
## Editor de texto
La interfaz gráfica se compone de un editor de texto con resaltado de sintaxis sql en el cual podemos escribir consultas 
## Arbol de Directorios
También se cuenta con un navegador en la barra lateral izquierda para poder visualizar las diferentes bases de datos a las que tenemos acceso


# Manual Técnico 
## Conexión con el servidor
se importa las clases necesarias para el funcionamiento del socket
```python
import socket
import sys
```
se utilizan dos parametros, el primero es el parametro **AF_INET** y el segundo es **SOCK_STREAM**, el primero referencia a la familia de direcciones ipv4, mientras que el segundo referencia a la protocolo de conexion TCP, por lo que se puede conectar a un servidor

```python
 try:
        conexion= socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        print("Conexion exitosamente creada")
    except socket.error as err:
        print("La creacion de la conexion fue un fracaso por: %conexion" %(err))
        #este es un puerto por defecto para el socket
    port= 80
```
Aca se puede observar la conexion, con la funcion **gethostbyname** se especifica el nombre del servidor, para conectar directamente con una direccion se utiliza la funcion **gethostbyaddr** la cual se conectara con la direccion especifica
```python
    try:
        host_ip= socket.gethostbyname('www.google.com')#conectandome con el servidor
        #PARA ENVIAR PAQUETES DE DATOS SE NECESITARA LA LIBRERIA SENDALL
    except socket.gaierror:
        print("Hubo un error en la conexion")
        sys.exit()
    conexion.connect((host_ip,port))
    print("Servidor conectado exitosamente" +str(port))
```
