## Accediendo al tablero de Grafana

El servicio de Grafana fue desplegado como de tipo ClusterIP.

Verifica el tipo de servicio de Grafana utilizando el siguiente comando:

```plain
k get svc grafana -n istio-system
```{{exec}}

Para poder acceder a la interfaz gráfica de Grafana, es necesario modificar el tipo del servicio a NodePort.

Para modificar el servicio de Grafana, utiliza el siguiente comando:

```plain
kubectl patch svc grafana -n istio-system -p '{"spec":{"type":"NodePort"}}'
```{{exec}}

Verifica nuevamente el tipo  de servicio de Grafana utilizando el siguiente comando:

```plain
k get svc grafana -n istio-system
```{{exec}}

Deberás obtener una salida similar a la siguiente:

```
kubectl get svc grafana -n istio-system
NAME      TYPE       CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
grafana   NodePort   10.107.230.195   <none>        3000:31294/TCP   5m20s
```
  
Identifica el puerto en el que se ha expuesto el servicio de grafana hacia el exterior. 
Para hacerlo, observa el número de puerto que se encuentra luego de 3000: en la columna PORT(S).
Para el ejemplo anterior, el puerto es 31294.
  
Del menú desplegable que se encuentra en la parte superior derecha de la ventana, selecciona *Traffic / Ports*
  
![Traffic / Ports](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step6/TrafficPorts.png?raw=true "Traffic / Ports")
  
En la ventana *Traffic Port Accessor*, ingresa el número de puerto en el campo *Custom Ports* y presiona el botón **ACCESS**.
  
![Traffic Port Accessor](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step6/TrafficPortsAccessor.png?raw=true "Traffic Port Accessor")

La ventana principal del tablero de grafana se abrirá en una nueva pestaña.
  
Para continuar presiona el botón **NEXT**
