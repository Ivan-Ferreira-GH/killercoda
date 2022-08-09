## Instalar Prometheus

El paquete de instalación de Istio proporciona archivos `yml` para la instalación de las herramientas de observabilidad en el directorio `istio-*.*.*/samples/addons`.

Para que Grana y Kiali funcionen, primero debes instalar Prometheus.

Para instalar Prometheus ejecuta el siguiente comando:

```plain
kubectl apply -f ~/istio-*.*.*/samples/addons/prometheus.yaml
```{{exec}}

Verifica que el *Pod* de Prometheus ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get po -l app=prometheus -n istio-system
```{{exec}}

Verifica que el *Service* de Prometheus ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get svc -l app=prometheus -n istio-system
```{{exec}}

Verifica que el *ServiceAccount* de Prometheus ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:

```plain
k get serviceaccount -l app=prometheus -n istio-system
```{{exec}}

Verifica que el *ConfigMap* de Prometheus ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get configmap -l app=prometheus -n istio-system
```{{exec}}

Verifica que el *ClusterRole* de Prometheus ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get configmap -l app=prometheus -n istio-system
```{{exec}}

Verifica que el *ClusterRoleBinding* de Prometheus ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get configmap -l app=prometheus -n istio-system
```{{exec}}

Para continuar presiona el botón **NEXT**
