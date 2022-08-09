## Instalar Grafana

El paquete de instalación de Istio proporciona archivos `yml` para la instalación de las herramientas de observabilidad en el directorio `istio-*.*.*/samples/addons`.

Para instalar Grafana ejecuta el siguiente comando:

```plain
kubectl apply -f ~/istio-*.*.*/samples/addons/grafana.yaml
```{{exec}}

Verifica que el *Pod* de Prometheus ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get po -l app=grafana -n istio-system
```{{exec}}

Verifica que el *Service* de Prometheus ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get svc grafana -n istio-system
```{{exec}}

Verifica que el *ServiceAccount* de Prometheus ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:

```plain
k get serviceaccount grafana -n istio-system
```{{exec}}

Verifica que el *ConfigMap* de Prometheus ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get configmap prometheus -n istio-system
```{{exec}}

Verifica que el *ClusterRole* de Prometheus ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get clusterrole -n istio-system
```{{exec}}

Verifica que el *ClusterRoleBinding* de Prometheus ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get clusterrolebinding -n istio-system
```{{exec}}

Para continuar presiona el botón **NEXT**
