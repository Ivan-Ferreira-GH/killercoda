## Instalar Zipkin

El paquete de instalación de Istio proporciona archivos `yml` para la instalación de las herramientas de observabilidad en el directorio `istio-*.*.*/samples/addons/extras`.

Para instalar Zipkin ejecuta el siguiente comando:

```plain
kubectl apply -f ~/istio-*.*.*/samples/addons/extras/zipkin.yaml
```{{exec}}

Verifica que el *Pod* de Zipkin ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get po -l app=zipkin -n istio-system
```{{exec}}

Verifica que los *Services* de Zipkin ha sidon desplegados en el *namespace* `istio-system` con el siguiente comando:
```plain
k get svc tracing zipkin -n istio-system
```{{exec}}

Para poder acceder a la interfaz gráfica de Zipkin, es necesario modificar el tipo del servicio a NodePort.

Para modificar el servicio de Zipkin, utiliza el siguiente comando:

```plain
kubectl patch svc zipkin -n istio-system -p '{"spec":{"type":"NodePort"}}'
```{{exec}}

Verifica nuevamente el tipo de servicio de Zipkin utilizando el siguiente comando:

```plain
k get svc zipkin -n istio-system
```{{exec}}

Deberás obtener una salida similar a la siguiente:

```
k get svc zipkin -n istio-system
NAME     TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)          AGE
zipkin   NodePort   10.99.77.189   <none>        9411:30956/TCP   3m40s
```
Identifica el puerto en el que se ha expuesto el servicio de Zipkin hacia el exterior. Para hacerlo, observa el número de puerto que se encuentra luego de 9411: en la columna PORT(S). Para el ejemplo anterior, el puerto es 30956.

Del menú desplegable que se encuentra en la parte superior derecha de la ventana, selecciona Traffic / Ports

![Traffic / Ports](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step10/TrafficPorts.png?raw=true "Traffic / Ports")
  
En la ventana *Traffic Port Accessor*, ingresa el número de puerto en el campo *Custom Ports* y presiona el botón **ACCESS**.

![Traffic Port Accessor](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step10/TrafficPortsAccessorZipkin.png?raw=true "Traffic Port Accessor")
  
La ventana principal de Zipkin se abrirá en una nueva pestaña.
  
Para continuar presiona el botón **NEXT**
