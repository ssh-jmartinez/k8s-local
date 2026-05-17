# 🚀 Mi Primer Cluster de Kubernetes con Minikube

¡Bienvenido! Si llegaste acá, es porque querés dejar de ver teoría y empezar a ensuciarte las manos con **Kubernetes**. 

En este repositorio te dejo todo lo necesario para que levantes tu primer cluster local y despliegues una aplicación con balanceo de carga en menos de 10 minutos.

---

## 📋 Prerrequisitos

Antes de empezar, asegurate de tener instalado:

1. **Docker**: El motor de contenedores que usaremos como driver. [Descargar aquí](https://www.docker.com/products/docker-desktop/).
2. **Kubectl**: La herramienta de línea de comandos para interactuar con el cluster. [Instalación](https://kubernetes.io/docs/tasks/tools/).
3. **Minikube**: La herramienta que nos permite correr K8s localmente. [Instalación](https://minikube.sigs.k8s.io/docs/start/).

---

## 🛠️ Paso a Paso

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
En este repo te dejé un archivo llamado deployment.yaml. Ejecutalo para crear los Pods y el Servicio:

