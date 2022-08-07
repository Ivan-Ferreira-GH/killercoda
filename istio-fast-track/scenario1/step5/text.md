## Crear el Virtual Service de Istio

Observa el contenido el archivo `~/istio-fast-track/istio-lab1/yml/istio-virtualservice-hello-world.yml`.

```plain
more ~/istio-fast-track/istio-lab1/yml/istio-virtualservice-hello-world.yml
```{{exec}}

El archivo `istio-virtualservice-hello-world.yml` creará:
* Un *Virtual Service* que
* Se vinculará con el gateway Istio
* Aceptará peticiones http
* Ruteará las peticiones a la aplicación web hello-world

Para aplicar la configuración ejecuta el siguiente comando:

```plain
kubectl apply -f ~/istio-fast-track/istio-lab1/yml/istio-virtualservice-hello-world.yml
```{{exec}}

Verifica que el servicio ha sido creado con el siguiente comando:

```plain
k get svc -o wide
```{{exec}}

Observa los detalles del gateway con el siguiente comando:

```plain
k describe gateway
```{{exec}}

Obtén la dirección IP del clúster con el siguiente comando:
```plain
kubectl get svc -l istio=ingressgateway -n istio-system
```{{exec}}

Si intentas conectarte a la aplicación utilizando `curl` a la dirección IP del clúster, ahora sí recibirás respuesta de la aplicación.
```plain
CLUSTER_IP=$(kubectl get svc -l istio=ingressgateway -n istio-system -o jsonpath='{.items[0].spec.clusterIP}')
curl http://$CLUSTER_IP && echo
```{{exec}}

Para continuar presiona el botón **NEXT**
