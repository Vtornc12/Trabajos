# Particionado MBR y GPT con fdisk

## Requisitos previos

Asegúrate de tener acceso root y `fdisk` instalado en tu sistema. Usa:

```bash
sudo -i
```

---

## Particionado MBR (100 GiB)

### 1. Verificar discos disponibles

```bash
lsblk
```

### 2. Seleccionar el disco y crear particiones

```bash
sudo fdisk /dev/sdb
```

- Crear tres particiones primarias:
  - `20 GiB` (n -> p -> 1 -> +20G)
  - `10 GiB` (n -> p -> 2 -> +10G)
  - `15 GiB` (n -> p -> 3 -> +15G)
- Crear una partición extendida con el resto del espacio (n -> e -> 4 -> ENTER)
- Dentro de la extendida, crear dos particiones lógicas:
  - `10 GiB` (n -> l -> +10G)
  - `15 GiB` (n -> l -> +15G)
- Guardar cambios (`w`).

### 3. Formatear en ext4

```bash
sudo mkfs.ext4 /dev/sdb1
sudo mkfs.ext4 /dev/sdb2
sudo mkfs.ext4 /dev/sdb3
sudo mkfs.ext4 /dev/sdb5
sudo mkfs.ext4 /dev/sdb6
```

### 4. Montar las particiones

```bash
sudo mkdir -p /media/sdb{1,2,3,5,6}
sudo mount /dev/sdb1 /media/sdb1
sudo mount /dev/sdb2 /media/sdb2
sudo mount /dev/sdb3 /media/sdb3
sudo mount /dev/sdb5 /media/sdb5
sudo mount /dev/sdb6 /media/sdb6
```

```bash
echo "Soy la partición 1 MBR y tengo un tamaño de 20GiB" | sudo tee /media/sdb1/info.txt
echo "Soy la partición 2 MBR y tengo un tamaño de 10GiB" | sudo tee /media/sdb2/info.txt
echo "Soy la partición 3 MBR y tengo un tamaño de 15GiB" | sudo tee /media/sdb3/info.txt
echo "Soy la partición 5 MBR y tengo un tamaño de 10GiB" | sudo tee /media/sdb5/info.txt
echo "Soy la partición 6 MBR y tengo un tamaño de 15GiB" | sudo tee /media/sdb6/info.txt
```

### 5. Modificar `/etc/fstab`

```bash
echo "UUID=d5aeec54-5d4a-4164-9783-d28bf23109d8 /media/sdb1 ext4 defaults 0 2" | sudo tee -a /etc/fstab
echo "UUID=3bc333c2-6c36-42c7-b1b7-cebd4fd66d6e /media/sdb2 ext4 defaults 0 2" | sudo tee -a /etc/fstab
echo "UUID=39763d05-58be-4074-acbc-4d14a5bde19e /media/sdb3 ext4 defaults 0 2" | sudo tee -a /etc/fstab
echo "UUID=93897ad0-ec81-4dab-9a42-15a54965086c /media/sdb5 ext4 defaults 0 2" | sudo tee -a /etc/fstab
echo "UUID=984d4a98-6227-4693-a420-bb04a755f996 /media/sdb6 ext4 defaults 0 2" | sudo tee -a /etc/fstab
```

---

## Particionado GPT (50 GiB)

### 1. Crear particiones con `parted`

```bash
sudo parted /dev/sdc mklabel gpt
sudo parted /dev/sdc mkpart primary ext4 1MiB 20GiB
sudo parted /dev/sdc mkpart primary ext4 20GiB 35GiB
```

### 2. Formatear en ext4

```bash
sudo mkfs.ext4 /dev/sdc1
sudo mkfs.ext4 /dev/sdc2
```

### 3. Montar particiones

```bash
sudo mkdir -p /media/sdc{1,2}
sudo mount /dev/sdc1 /media/sdc1
sudo mount /dev/sdc2 /media/sdc2
```

```bash
echo "Soy la partición 1 GPT y tengo un tamaño de 20GiB" | sudo tee /media/sdc1/info.txt
echo "Soy la partición 2 GPT y tengo un tamaño de 15GiB" | sudo tee /media/sdc2/info.txt
```

### 4. Modificar `/etc/fstab`

```bash
echo "UUID=a17a2144-f7e0-465c-99da-552e73151a40 /media/sdc1 ext4 defaults 0 2" | sudo tee -a /etc/fstab
echo "UUID=d368701c-622b-4c57-8e67-bdc53b0888d0 /media/sdc2 ext4 defaults 0 2" | sudo tee -a /etc/fstab
```

---
