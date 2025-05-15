# 🖥️ HARDWARE – PRÁCTICA CHROOT

## 🔧 Instalamos la máquina Debian
   
---
![Imagen1](img/img1.png)


## 🍥 Instalación de Debian
   
---
![Debian](img/db1.png)

![Debian](img/db2.png)

![Debian](img/db3.png)

![Debian](img/db4.png)

![Debian](img/db5.png)

![Debian](img/db6.png)

![Debian](img/db7.png)

![Debian](img/db8.png)

![Debian](img/db9.png)

![Debian](img/db10.png)

![Debian](img/db11.png)

![Debian](img/db12.png)

![Debian](img/db13.png)

![Debian](img/db14.png)

![Debian](img/db15.png)

![Debian](img/db16.png)

![Debian](img/db17.png)

![Debian](img/db18.png)

![Debian](img/db19.png)

![Debian](img/db20.png)

![Debian](img/db21.png)

![Debian](img/db22.png)

![Debian](img/db23.png)

![Debian](img/db24.png)

![Debian](img/db25.png)

![Debian](img/db26.png)

![Debian](img/db27.png)

![Debian](img/db28.png)

![Debian](img/db29.png)

![Debian](img/db30.png)

---

## 🛠️ Instalamos el disco Kali en la máquina Debian

![Imagen](img/img2.png)

---

## 😼​ Kali

Desde kali cambiaremos el idioma al español con "setxbkmap es" y con sudo su comprobamos con /dev

![Kali](img/kl1.png)

Creamos el directorio /mnt/recuperar y montamos la particion del disco en el

![Kali](img/kl2.png)

Montamos la particion 1 del disco en el directorio que acabamos de crear

![Kali](img/kl3.png)

🟥 **Dev:** _Montamos el directorio /dev dentro de la ruta /dev/recuperar/dev._

🟦 **Proc:** _Montamos el directorio /proc dentro de /mnt/recuperar/proc._

🟧 **Sys:** _Montamos el directorio /sys dentro de /mnt/recuperar/sys._

![Kali](img/kl4.png)

Creamos una jaula con el comando chroot /mnt/recuperar, lo que nos permite trabajar dentro del sistema instalado en el disco (/dev/sda) como si fuera el único entorno, aislándonos de la Live.

![Kali](img/kl5.png)

Creamos una archivo para ver si cuando volvemos a Debian los cambios se han guardado 

![Kali](img/kl6.png)

---

## 💽 Quitamos el disco de Kali
  
![Imagen](img(img3)

---

## ✅ Verificación final

Y comprobamos que lo que hicimos desde Kali se ha guardado correctamente y es accesible desde Debian.

![Debian](img/db31.png)

