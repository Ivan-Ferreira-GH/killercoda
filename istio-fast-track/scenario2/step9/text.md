## Visualizando métricas en Zipkin

Mantén el comando `curl` activo en *Tab 1*.

En *Tab 2* instala Zipkin con el siguiente comando:

```plain
kubectl apply -f ~/istio-*.*.*/samples/addons/extras/zipkin.yaml
```{{exec}}

Verifica el tipo de servicio de Zipkin utilizando el siguiente comando:

```plain
k get svc zipkin -n istio-system
```{{exec}}

Para poder acceder a la interfaz gráfica de Zipkin, es necesario modificar el tipo del servicio a NodePort.
Para modificar el servicio de Zipkin, utiliza el siguiente comando:

```plain
kubectl patch svc zipkin -n istio-system -p '{"spec":{"type":"NodePort"}}'
```{{exec}}

Verifica nuevamente el tipo  de servicio de Grafana utilizando el siguiente comando:

```plain
k get svc zipkin -n istio-system
```{{exec}}

Deberás obtener una salida similar a la siguiente:

```
k get svc zipkin -n istio-system
NAME     TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
zipkin   NodePort   10.110.156.28   <none>        9411:30470/TCP   9s
```

Identifica el puerto en el que se ha expuesto el servicio de Zipkin hacia el exterior. 
Para hacerlo, observa el número de puerto que se encuentra luego de 9411: en la columna PORT(S).
Para el ejemplo anterior, el puerto es 30470.
  
Del menú desplegable que se encuentra en la parte superior derecha de la ventana, selecciona *Traffic / Ports*
  
![Traffic / Ports](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step9/TrafficPorts.png?raw=true "Traffic / Ports")
  
En la ventana *Traffic Port Accessor*, ingresa el número de puerto en el campo *Custom Ports* y presiona el botón **ACCESS**.
  
![Traffic Port Accessor](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step9/TrafficPortsAccessorZipkin.png?raw=true "Traffic Port Accessor")
La ventana principal de Zipkin se abrirá en una nueva pestaña.
  
Para continuar presiona el botón **NEXT**
