## Instalar la aplicación Web Customers

Instala una aplicación web de dos capas para poder observar las métricas a través de Grafana.

La arquitectura de la aplicación es la siguiente:

![Customers Wep Application](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/web-frontend.png?raw=true "Customers Web Application")

Observa el contenido del archivo `~/istio-fast-track/istio-lab2/yml/gateway.yml`.
Identifica el puerto, el protocolo y el host que ha sido configurado.

```plain
more ~/istio-fast-track/istio-lab2/yml/gateway.yml
```{{exec}}

Despliega el gateway de Istio con el siguiente comando:

```plain
kubectl apply -f ~/istio-fast-track/istio-lab2/yml/gateway.yml
```{{exec}}

Verifica el despliegue del gateway con el siguiente comando:
```plain
k get gateway
```{{exec}}

Observa los detalles del gateway con el siguiente comando:
```plain
k describe gateway
```{{exec}}

Observa el contenido del archivo `~/istio-fast-track/istio-lab2/yml/web-frontend.yml`
```plain
more ~/istio-fast-track/istio-lab2/yml/web-frontend.yml
```{{exec}}

Despliega el Pod, Service y VirtualService para *web-frontend* con el siguiente comando:
```plain
kubectl apply -f ~/istio-fast-track/istio-lab2/yml/web-frontend.yml
```{{exec}}

Observa el contenido del archivo `~/istio-fast-track/istio-lab2/yml/customers.yml`
Identifica el recurso *DestionationRule*. Este recurso establece el ruteo hacia la aplicación *customers* versión 1. 

```plain
more ~/istio-fast-track/istio-lab2/yml/customers.yml
```{{exec}}

Despliega el Pod, Service, VirtualService y DestinationRule para web-frontend con el siguiente comando:
```plain
kubectl apply -f ~/istio-fast-track/istio-lab2/yml/customers.yml
```{{exec}}

Verfica el despliegue de las aplicaciones con el siguiente comando:
```plain
k get pods
```{{exec}}

Para continuar presiona el botón **NEXT**
