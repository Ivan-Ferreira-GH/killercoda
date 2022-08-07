## Crear el Virtual Service de Istio

Observa el contenido el archivo `~/istio-fast-track/istio-lab1/yml/istio-virtualservice-hello-world.yml`.

```plain
more ~/istio-fast-track/istio-lab1/yml/istio-virtualservice-hello-world.yml
```{{exec}}

El archivo `istio-virtualservice-hello-world.yml` creará:
* Un *Virtual Service* que...
* Se vinculará con el gateway Istio
* Aceptará peticiones http
* Ruteará las peticiones a la aplicación web hello-world

Para aplicar la configuración ejecuta el siguiente comando:

```plain
kubectl apply -f ~/istio-fast-track/istio-lab1/yml/istio-virtualservice-hello-world.yml
```{{exec}}

Verifica que el servicio ha sido creado con el siguiente comando:

```plain
k get vs
```{{exec}}

Si intentas conectarte a la aplicación utilizando `curl` a la dirección IP del clúster, ahora sí recibirás respuesta de la aplicación.
```plain
CLUSTER_IP=$(kubectl get svc -l istio=ingressgateway -n istio-system -o jsonpath='{.items[0].spec.clusterIP}')
curl http://$CLUSTER_IP && echo
```{{exec}}

Ejecuta nuevamente el comando `curl` con la opción `-v`:
```plain
curl -v http://$CLUSTER_IP && echo
```{{exec}}

Observa el resultado de la cabecera de la respuesta indicando server: `istio-envoy`.
```
* Trying 10.110.184.32:80...
* TCP_NODELAY set
* Connected to 10.110.184.32 (10.110.184.32) port 80 (#0)
> GET / HTTP/1.1
> Host: 10.110.184.32
> User-Agent: curl/7.68.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< date: Sun, 07 Aug 2022 14:52:32 GMT
< content-length: 11
< content-type: text/plain; charset=utf-8
< x-envoy-upstream-service-time: 0
< server: istio-envoy
< 
* Connection #0 to host 10.110.184.32 left intact
Hello World
```
Esto confirma que la petición a pasado a través del proxy *Envoy*.

Para continuar presiona el botón **NEXT**
