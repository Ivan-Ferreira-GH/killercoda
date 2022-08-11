# Visualizar la inyección de retardos

Inyectarás un retardo de 5 segundos al servicio *Customers* para el 50% de todas las peticiones a través de su *VirtualService*.

Asegúrate de que en *Tab 1* se encuentra en ejecución el comando `curl`.

```plain
INGRESS_GATEWAY=$(k get service istio-ingressgateway -n istio-system -o jsonpath='{.spec.clusterIP}')
while true; do curl http://$INGRESS_GATEWAY; done
```{{exec}}

Observa el contenido del archivo `~/istio-fast-track/istio-lab2/yml/customers-delay.yml` e identifica la configuración establecida en la sección `fault`.

```plain
more ~/istio-fast-track/istio-lab2/yml/customers-delay.yml
```{{exec}}

Aplica la configuración del VirtualService para inyectar un retardo de 5 segundos con el siguiente comando:

```plain
kubectl apply -f ~/istio-fast-track/istio-lab2/yml/customers-delay.yml
```{{exec}}

En Grafana, presiona sobre *Home*, selecciona la carpeta *Istio* y luego *Istio Service Dashboards*.
Para el campo *Service* selecciona *web-frontend.default.svc.cluster.local* de la lista desplegable.

Expande el panel *Client Workloads*. Notarás una duración incrementada en el gráfico *Incoming Request Duration*.

![Incoming Request](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step11/IncomingDelay.png?raw=true "Incoming Request")

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

