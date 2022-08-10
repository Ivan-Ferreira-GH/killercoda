## Instalar Kiali

El paquete de instalación de Istio proporciona archivos `yml` para la instalación de las herramientas de observabilidad en el directorio `istio-*.*.*/samples/addons`.

Para instalar Kiali ejecuta el siguiente comando:

```plain
kubectl apply -f ~/istio-*.*.*/samples/addons/kiali.yaml
```{{exec}}

Verifica que el *Pod* de Kiali ha sido desplegado en el *namespace* `istio-system` con el siguiente comando:
```plain
k get po -l app=kiali -n istio-system
```{{exec}}

Verifica que el *Service* de Kiali ha sidon desplegados en el *namespace* `istio-system` con el siguiente comando:
```plain
k get svc kiali -n istio-system
```{{exec}}

Para poder acceder a la interfaz gráfica de Kiali, es necesario modificar el tipo del servicio a NodePort.

Para modificar el servicio de Kiali, utiliza el siguiente comando:

```plain
kubectl patch svc kiali -n istio-system -p '{"spec":{"type":"NodePort"}}'
```{{exec}}

Verifica nuevamente el tipo de servicio de Kiali utilizando el siguiente comando:

```plain
k get svc kiali -n istio-system
```{{exec}}

Deberás obtener una salida similar a la siguiente:
```
k get svc kiali -n istio-system
NAME    TYPE       CLUSTER-IP      EXTERNAL-IP   PORT(S)                          AGE
kiali   NodePort   10.107.234.42   <none>        20001:32542/TCP,9090:32508/TCP   115s
```
Identifica el puerto en el que se ha expuesto el servicio de Kiali hacia el exterior. Para hacerlo, observa el número de puerto que se encuentra luego de 20001: en la columna PORT(S). Para el ejemplo anterior, el puerto es 32542.

Del menú desplegable que se encuentra en la parte superior derecha de la ventana, selecciona Traffic / Ports

![Traffic / Ports](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step11/TrafficPorts.png?raw=true "Traffic / Ports")
  
En la ventana *Traffic Port Accessor*, ingresa el número de puerto en el campo *Custom Ports* y presiona el botón **ACCESS**.

![Traffic Port Accessor](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario2/step11/TrafficPortsAccessorKiali.png?raw=true "Traffic Port Accessor")
  
La ventana principal de Kiali se abrirá en una nueva pestaña.
  
Para continuar presiona el botón **NEXT**
