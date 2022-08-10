## Observando métricas con Grafana

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
  
Del menú 
