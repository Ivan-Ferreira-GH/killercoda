## Visualizando métricas de Web Frontend en Grafana

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
En el campo *Service*, selecciona *web-frontend.default.svc.cluster.local* de la lista desplegable y explora las métricas.

![Grafana Web Frontend](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step7/GrafanaWebFrontEnd.png?raw=true "Grafana Web Frontend")

Para continuar presiona el botón **NEXT**
