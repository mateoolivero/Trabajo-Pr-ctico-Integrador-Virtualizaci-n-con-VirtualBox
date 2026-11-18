# Trabajo Práctico Integrador: Virtualización con VirtualBox 🖥️⚙️

Repositorio correspondiente al Trabajo Práctico Integrador (**Instancia: Recuperatorio - Noviembre de 2026**) de la materia **Arquitectura y Sistemas Operativos**, perteneciente a la **Tecnicatura Universitaria en Programación a Distancia (TUPaD)** de la **Universidad Tecnológica Nacional (UTN)**.

---

## 👥 Integrantes del Grupo y Cátedra

* **Olivero, Mateo** — `mateoolivero09@gmail.com` — **Comisión 5** (Prof. Patricio Costello)
* **Ramírez, Iván Francisco** — `ivan.rama.pef@gmail.com` — **Comisión 14** (Prof. Mauricio Gabriel Pasti)

---

## 📋 Descripción del Proyecto

Este proyecto documenta la fundamentación teórica y la implementación práctica de la virtualización de hardware utilizando el hipervisor de **Tipo 2** **Oracle VirtualBox** sobre un sistema anfitrión **Windows**.

El caso práctico consistió en el despliegue y configuración integral de una máquina virtual denominada **`Ubuntu.AySO`** con **Ubuntu Server 25.04 (Plucky Puffin) 64-bit**, abarcando los siguientes pilares técnicos:

* **Configuración de Hardware Virtual:** Asignación de 4 GB (4096 MB) de memoria RAM base, 2 núcleos de procesamiento, disco duro virtual VDI de reserva dinámica de 40 GB (controladora SATA), interfaz de paravirtualización KVM y aceleración por hardware con paginación anidada habilitada.
* **Redes Virtuales:** Configuración de un adaptador de red (Intel PRO/1000 MT Desktop) en **modo Adaptador Puente (Bridge)**, logrando la integración transparente a la red local (`192.168.1.0/24`) con asignación directa de dirección IP por DHCP (`192.168.1.52`).
* **Despliegue de Servicios Web:** Instalación, habilitación (`systemd`) y puesta en marcha del servidor web **Apache (`apache2`)**, validando su accesibilidad HTTP en el puerto 80 tanto desde el navegador del equipo anfitrión como desde dispositivos externos (teléfono móvil) conectados a la misma red local.
* **Gestión y Respaldo (Snapshots):** Creación de una instantánea del estado funcional verificada bajo el nombre **`"servidor apache funcionando OK"`** como punto seguro de restauración.

---

## 📂 Estructura del Repositorio

* **`TPI_Virtualizacion_Olivero_Ramirez_Recuperatorio.pdf`**: Documento de informe técnico completo que desarrolla el marco teórico (requisitos de Popek y Goldberg, anillos de protección, técnicas de virtualización, tipos de hipervisores y redes), el desarrollo metodológico paso a paso, los resultados, las conclusiones y los anexos con capturas de pantalla y diagramas de red.
* **`README.md`**: Documentación principal del repositorio, ficha técnica del proyecto, presentación del equipo y enlaces de acceso directo.

---

## 🔗 Enlaces del Proyecto

* **Repositorio oficial en GitHub:** [Ver Repositorio en GitHub](https://github.com/mateoolivero/Trabajo-Pr-ctico-Integrador-Virtualizaci-n-con-VirtualBox)
* **Video Explicativo:** [Ver Grabación en Google Drive](https://drive.google.com/file/d/1KEcyxFU4RXP1cJsI_FPZ7WyeQHxcdWVf/view?usp=sharing)

---

## 🛠️ Comandos Principales Utilizados

Para el aprovisionamiento y diagnóstico del servidor web dentro de Ubuntu Server:

```bash
# Actualización de repositorios e instalación de Apache
sudo apt update
sudo apt install -y apache2

# Habilitación e inicio del servicio
sudo systemctl enable apache2
sudo systemctl start apache2

# Diagnóstico de estado y verificación de interfaz de red
systemctl status apache2 --no-pager
ip addr