# Visualizar la inyección de errores

Inyectarás errores en las peticiones al servicio *Customers* para el 50% de todas las peticiones a través de su *VirtualService*.

Asegúrate de que en *Tab 1* se encuentra en ejecución el comando `curl`.

```plain
INGRESS_GATEWAY=$(k get service istio-ingressgateway -n istio-system -o jsonpath='{.spec.clusterIP}')
while true; do curl http://$INGRESS_GATEWAY; done
```{{exec}}

Observa el contenido del archivo `~/istio-fast-track/istio-lab2/yml/customers-fault.yml` e identifica la configuración establecida en la sección `fault`.

```plain
more ~/istio-fast-track/istio-lab2/yml/customers-fault.yml
```{{exec}}

Aplica la configuración del VirtualService para inyectar errores al 50% de las peticiones con el siguiente comando:

```plain
kubectl apply -f ~/istio-fast-track/istio-lab2/yml/customers-fault.yml
```{{exec}}

En **Tab 1** notarás que algunas peticiones retornan `"Request failed with status code 500"`.

En Grafana, presiona sobre *Home*, selecciona la carpeta *Istio* y luego *Istio Service Dashboards*.
Para el campo *Service* selecciona *customers.default.svc.cluster.local* de la lista desplegable.
Para el campo *Reporter* selecciona *source*.


Expande el panel *General*. Notarás una caída de la tasa de éxito en *Client Success Rate (non-5xx response)*.

![Grafana Success Rate](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step12/GrafanaSucessRateDrop.png?raw=true "Grafana Success Rate")

Observa como este retardo se visualiza en Zipkin.
En la pantalla principal de Zipkin, presiona sobre el signo **+** del panel superior, selecciona *ServiceName* y luego *web-frontend.default* de la lista desplegable.
Presiona el botón *RUN QUERY*.

Las trazas con error se mostrarán en color rojo.

![Zipkin Query](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step12/ZipkinErrorTrace.png?raw=true "Zipkin Query")

Observa cómo se visualizan los errores en Kiali.
En la pantalla principal de Kiali, selecciona *Graph* del panel derecho.
En el panel superior, presiona sobre el campo *Namespace* y selecciona *Default* de la lista desplegable.

Notarás que el servicio *web-frontend* tiene un borde de color rojo.

![Kiali](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step12/Kiali.png?raw=true "Kiali")

Si presionas sobre el servicio *web-fronend* y observas el panel lateral derecho, encontrarás los detalles de las peticiones HTTP.
El gráfico muestra el porcentaje de éxitos y fallos. Ambos números deben encontrarse alrededor de 50%, que corresponde con el valor establecido en el *VirtualService*.

Para continuar presiona el botón **NEXT**
