## Visualizando métricas en Grafana

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
En la sección superior izquierda, presiona sobre *General / Home* y luego presiona sobre la carpeta *Istio*.
