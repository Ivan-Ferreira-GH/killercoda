# Visualizar la inyección de fallos y retardos

Inyectarás un retardo de 5 segundos al servicio *Customers* para el 50% de todas las peticiones a través de su *VirtualService*.
Observa el contenido del archivo `~/istio-fast-track/istio-lab2/yml/customers-delay.yml` e identifica la configuración establecida en la sección `fault`.

```plain
more ~/istio-fast-track/istio-lab2/yml/customers-delay.yml
```{{exec}}

Asegúrate de que en *Tab 1* se encuentra en ejecución el comando `curl`.

```plain
INGRESS_GATEWAY=$(k get service istio-ingressgateway -n istio-system -o jsonpath='{.spec.clusterIP}')
while true; do curl http://$INGRESS_GATEWAY; done
```{{exec}}

En Grafana, presiona sobre *Home*, selecciona la carpeta *Istio* y luego *Istio Service Dashboards*.
Para el campo *Service* selecciona *web-frontend.default.svc.cluster.local* de la lista desplegable.

Expande el panel *Client Workloads*. Notarás una duración incrementada en el gráfico *Incoming Request Duration*.

![Incoming Request](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step11/IncomingDelay.png?raw=true "Incoming Request")

