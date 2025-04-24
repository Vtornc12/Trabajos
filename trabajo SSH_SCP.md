# 🖥️ Trabajo con SSH y SCP

Este documento describe paso a paso la configuración y uso de SSH y SCP entre dos máquinas virtuales.

---

## 🔧 **Hardware y configuración de red**

**Configuramos las dos clonaciones enlazadas**, asignándoles los puertos correspondientes y colocándolas en el adaptador 2 como **red interna**:

![Configuración de red](images/image1.png)

---

## 👤 **Creación de usuarios**

Creamos ambos usuarios en cada máquina:

![Usuarios creados](images/image2.png)

---

## 🛠️ **Corrección de la configuración**

Accedemos a la máquina A y la configuramos

![Configuración corregida](images/image3.png)

---

## 🔐 **Conexión SSH desde máquina A a máquina B**

Desde la máquina A, accedemos a la máquina B utilizando SSH:

![SSH A → B](images/image4.png)

---

## 📁 **Creación y transferencia de archivos**

### 📄 **1. Crear `prueba` en máquina B**
Creamos el archivo `prueba` en la máquina B:

![Crear archivo en B](images/image5.png)

### 🔁 **2. Transferir `prueba` de B a A**
Usamos `scp` para transferir el archivo a la máquina A:

![Transferencia B → A](images/image6.png)

### 📄 **3. Crear `prueba2` en máquina A**
Desde la máquina A, creamos el archivo `prueba2` para transferirlo a la máquina B:

![Crear archivo en A](images/image7.png)

### 📄 ** Pasar `prueba` y  `prueba2` al escritorio**

Ahora pasaremos ambos archivos directamente al escritorio

![Transferir carpeta prueba](images/imageA.png)

![Transferir carpeta prueba2](images/imageB.png)

![Resultado](images/Result.png)

### 📂 **4. Crear y transferir carpeta `prueba3`**
Creamos una carpeta llamada `prueba3` con 200 archivos dentro:

![Crear carpeta con archivos](images/image8.png)

Transferimos la carpeta `prueba3` al escritorio:

![Transferir carpeta](images/image9.png)

---

## ✅ **Verificación final**

Comprobamos que la carpeta `prueba3` se haya copiado correctamente al escritorio:

![Carpeta en escritorio](images/image10.png)

---

## 📝 **Notas finales**

> ⚠️ **Nota:** Me he confundido creando `prueba1` en la máquina 2 y `prueba2` en la máquina 1, pero **el funcionamiento fue el mismo**.

---

