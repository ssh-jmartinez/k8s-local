# 🚀 Mi Primer Cluster de Kubernetes con Minikube

¡Bienvenido! Si llegaste acá, es porque querés dejar de ver teoría y empezar a ensuciarte las manos con **Kubernetes**. 

En este repositorio te dejo todo lo necesario para que levantes tu primer cluster local y despliegues una aplicación con balanceo de carga en menos de 10 minutos.

---

## 📋 Prerrequisitos

Antes de empezar, asegurate de tener instalado:

1. **Docker**: El motor de contenedores que usaremos como driver (asegurate de tener la app de Docker corriendo). [Descargar aquí](https://docs.docker.com/engine/install/).
2. **Kubectl**: La herramienta de línea de comandos para interactuar con el cluster. [Instalación](https://kubernetes.io/docs/tasks/tools/).
3. **Minikube**: La herramienta que nos permite correr K8s localmente. [Instalación](https://minikube.sigs.k8s.io/docs/start/).

---

## 🛠️ Paso a Paso

### 0. Clonar el repositorio
Primero, traete el proyecto a tu máquina local y parate dentro de la carpeta:
```bash
git clone https://github.com/ssh-jmartinez/k8s-local.git
cd k8s-local
```

### 1. Iniciar el Cluster
Abrí tu terminal y ejecutá el siguiente comando para levantar Kubernetes usando Docker como base:

```bash
minikube start --driver=docker
```

### 2. Verificar el estado
Asegurate de que tu nodo esté listo:
```bash
kubectl get nodes
```

### 3. Desplegar la Aplicación
Dentro de la carpeta **manifests/** vas a encontrar los archivos **deployment.yaml** y **service.yaml**. Ejecutá el siguiente comando para aplicar la configuración:
```bash
kubectl apply -f manifests/
```
<sub>(Tip: Al pasarle la carpeta completa, Kubernetes aplica todos los archivos yaml que encuentre adentro en un solo comando).</sub>

### 4. Verificamos que los pods se encuentren en **Running**
Asegurate de que los Pods cambien su estado a Running (puede tardar unos segundos la primera vez mientras se descarga la imagen):
```bash
kubectl get pods -w
```
<sub>(Nota: El flag -w o --watch te permite ver los cambios de estado en tiempo real. Salí con Ctrl + C cuando estén listos).</sub>

### 5. Acceder a la App
Como estamos en local, necesitamos que Minikube nos dé una URL para ver nuestra app en el navegador:
```bash
minikube service landing-page-service
```
<sub>💡 Nota: Este comando dejará la terminal ocupada manteniendo el túnel abierto. Si querés interactuar de nuevo con el cluster, abrí una nueva pestaña en tu terminal.</sub>

---

## 🧹 Limpieza

Cuando termines de jugar y quieras liberar espacio y memoria en tu compu, podés borrar la aplicación o directamente apagar el cluster:

* **Borrar solo la app (manteniendo Minikube vivo):**

  ```bash
  kubectl delete -f manifests/
  ``` 
* **Apagar el cluster (guarda el estado actual):**

  ```bash
  minikube stop
  ``` 
* **Borrar el cluster por completo (libera todo el espacio):**

  ```bash
  minikube delete
  ``` 
