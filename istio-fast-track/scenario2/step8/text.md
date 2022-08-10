## Visualizando métricas de Customers en Grafana

Obtén la dirección IP del *Ingress* con el siguiente comando:

```plain
INGRESS_GATEWAY=$(k get service istio-ingressgateway -n istio-system -o jsonpath='{.spec.clusterIP}')
```{{exec}}

Verifica la dirección IP obtenida con el siguiente comando:

```plain
echo $INGRESS_GATEWAY
```{{exec}}

Ejecuta el siguiente comando para generar carga sobre la aplicación utilizando `curl`:

```plain
while true; do curl http://$INGRESS_GATEWAY; done
```{{exec}}

Accede a la pestaña que muestra el tablero de Grafana. 
En la sección superior izquierda, presiona sobre *General / Home*.

![Grafana Home](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step7/GrafanaHome.png?raw=true "Grafana Home")

Luego selecciona la carpeta *Istio*.

![Grafana Istio](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step7/GrafanaIstioFolder.png?raw=true "Grafana Istio")

De la lista que aparece, selecciona Istio Service Dashboard.
En el campo *Service*, selecciona *customers.default.svc.cluster.local* de la lista desplegable y explora las métricas.

![Grafana Customers](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step8/GrafanaCustomers.png?raw=true "Grafana Customers")

Manteniendo el comando curl en ejecución en Tab 1, abre una nueva terminal presionado sobre el signo + en la parte superior izquierda de la ventana de la terminal.

![Tab 2](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step8/tab2.png?raw=true "Tab 2")

En *Tab 2* ejecuta el siguiente comando para eliminar el recurso *DestionationRule*:

```plain
k delete destinationrule customers
```{{exec}}

En *Tab 1* observa el mensaje de error recibido por parte de la aplicación.
Debido a que has eliminado el *DestionationRule*, recibirás el error `"Request failed with status code 503"`

Observa nuevamente las métricas en Grafana. Notarás una caida total de las peticiones entrantes.

![Grafana Customers](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step8/GrafanaCustomersDown.png?raw=true "Grafana Customers")

En *Tab 2* despliega nuevamente el *DestinationRule* con el siguiente comando:
```plain
kubectl apply -f ~/istio-fast-track/istio-lab2/yml/customers.yml
```{{exec}}

En *Tab 1* verifica que la aplicación responde nuevamente al comando curl.
En Grafana, verifica el restablecimiento de las peticiones para *customers.default.svc.cluster.local*.

Para continuar presiona el botón **NEXT**
