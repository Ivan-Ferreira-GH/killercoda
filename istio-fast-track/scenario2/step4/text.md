## Instalar Grafana

El paquete de instalación de Istio proporciona archivos `yml` para la instalación de las herramientas de observabilidad en el directorio `istio-*.*.*/samples/addons`.

Para instalar Grafana ejecuta el siguiente comando:

```plain
kubectl apply -f ~/istio-*.*.*/samples/addons/grafana.yaml
```{{exec}}

Verifica que el *Pod* de Grafana ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get po -l app=grafana -n istio-system
```{{exec}}

Verifica que el *Service* de Grafana ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get svc grafana -n istio-system
```{{exec}}

Verifica que el *ServiceAccount* de Grafana ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:

```plain
k get serviceaccount grafana -n istio-system
```{{exec}}

Verifica que los *ConfigMap* de Grafana han sido desplegados en el *namespace* `istio-system` con el siguiente comando:
```plain
k get configmap grafana istio-grafana-dashboards istio-services-grafana-dashboards -n istio-system
```{{exec}}

Para continuar presiona el botón **NEXT**
