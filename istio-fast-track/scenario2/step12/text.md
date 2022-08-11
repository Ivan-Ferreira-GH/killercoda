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
En la pantalla principal de Zipkin, presiona sobre el signo **+** del panel superior, selecciona **ServiceName** y luego *web-frontend.default* de la lista desplegable.
Luego agrega **minDuration** y establece **5s**.
Presiona el botón **RUN QUERY**.

![Zipkin Query](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step11/ZipkinQuery.png?raw=true "Zipkin Query")

Haz clic sobre alguna de las trazas y presiona el botón **SHOW** que se encuentra a la derecha para abrir la página de detalles.
En la página de detalles podrás notar que la petición duró 5 segundos en total.

![Zipkin Trace](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step11/IstioZipkinTrace.png?raw=true "Zipkin Trace")

La traza se compone de cuatro *spans*. Selecciona el tercer *span* que representa la petición hecha desde el servicio **web-frontend** al servicio **customers**.

En el panel lateral derecho, notarás que en la etiqueta **response_flags** está establecida a **DI**. 
DI significa **Delay Injection** e indica que la petición ha sido retardada.

![Zipkin DI](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step11/ZipkinDI.png?raw=true "Zipkin DI")

Para continuar presiona el botón **NEXT**
