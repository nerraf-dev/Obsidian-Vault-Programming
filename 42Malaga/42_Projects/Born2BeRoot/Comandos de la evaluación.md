# Comandos de la evaluación ⌨️

## 1. Comprobar que no haya ninguna interfaz gráfica en uso
Utilizaremos el comando `ls /usr/bin/*session` y nos debe aparecer el mismo resultado que en la captura. Si aparece algo diferente se está utilizando una interfaz gráfica.

[![Screen Shot 2022-11-25 at 12 00 02 AM](https://user-images.githubusercontent.com/66915274/203872315-0e87428b-5c5a-475b-9d7c-350eafbe3bea.png)](https://user-images.githubusercontent.com/66915274/203872315-0e87428b-5c5a-475b-9d7c-350eafbe3bea.png)
## 2. Comprobar que el servicio UFW está en uso

`sudo ufw status`

![Screen Shot](https://user-images.githubusercontent.com/66915274/203668014-bd228793-3532-4494-8b01-d046e4930c10.png)

`sudo service ufw status`

![Screen Shot](https://user-images.githubusercontent.com/66915274/203668066-6a3420d4-ae72-4263-8474-2e4946e2367a.png)

## 3. Comprobar que el servicio SSH está en uso.

`sudo service ssh status`

![Screen Shot](https://user-images.githubusercontent.com/66915274/203668165-e642c21f-a11e-48b1-bed5-83639445251e.png)



## 4. Comprobar que utilizas el sistema operativo Debian o CentOS.

`uname -v`
`uname --kernel-version`

![Screen Shot](https://user-images.githubusercontent.com/66915274/203669122-0be5033c-c882-4a2e-bf22-6a680f998a56.png)

## 5. Comprobar que tu usuario esté dentro de los grupos "sudo" y "user42".

`getent group sudo`

`getent group user42`

![Screen Shot](https://user-images.githubusercontent.com/66915274/203680444-5fb18ae1-724e-4f78-a77f-a0f5bcc04913.png)


## 6. Crear un nuevo usuario y mostrar que sigue la política de contraseñas que hemos creado.

`sudo adduser name_user` e introducimos una contraseña que siga la política.

![Screen Shot](https://user-images.githubusercontent.com/66915274/203680847-b4555fd4-f847-4bce-b944-edf3e7720c99.png)


## 7. Creamos un nuevo grupo llamado "evaluating".

`sudo addgroup evaluating`

![Screen Shot](https://user-images.githubusercontent.com/66915274/203680980-784b2b60-82f4-405a-9f07-ec4948e86868.png)


## 8. Añadimos el nuevo usuario al nuevo grupo.

`sudo adduser name_user evaluating`

![Screen Shot](https://user-images.githubusercontent.com/66915274/203680980-784b2b60-82f4-405a-9f07-ec4948e86868.png)


Para comprobar que se haya introducido correctamente.

![Screen Shot](https://user-images.githubusercontent.com/66915274/203681267-106e4d37-0ec4-4006-95a4-88dd7109c4b6.png)


## 9. Comprobar que el hostname de la máquina es correcto login42.

![Screen Shot](https://user-images.githubusercontent.com/66915274/203681701-4f9b9ff1-28b6-4d06-9489-f930eee4b6e5.png)


## 10. Modificar hostname para reemplazar tu login por el del evaluador. En este caso lo reemplazaré por student42.

`sudo nano /etc/hostname` y reemplazamos nuestro login por el nuevo.



`sudo nano /etc/hosts` y reemplazamos nuestro login por el nuevo.



Reiniciamos la máquina.



Una vez nos hemos logueado de nuevo podemos ver como el hostname se ha cambiado correctamente.












