## Configurar el Gateway de Istio

Observa el contenido el archivo `~istio-fast-track/istio-lab1/yml/istio-gateway.yml`.

```plain
more ~/istio-fast-track/istio-lab1/yml/istio-gateway.yml
```{{exec}}

El archivo `istio-gateway.yml` creará:
* Un *Ingress Gateway* que...
* Aceptará peticiones hacia el puerto 80

El `'*'` en `hosts:` permitirá la conexión a través de la dirección IP en lugar de utilizar la resolución de nombres DNS.

Para aplicar la configuración ejecuta el siguiente comando:

```plain
kubectl apply -f ~/istio-fast-track/istio-lab1/yml/istio-gateway.yml
```{{exec}}

Verifica que el gateway ha sido creado con el siguiente comando:

```plain
k get gateway
```{{exec}}

Observa los detalles del gateway con el siguiente comando:

```plain
k describe gateway
```{{exec}}

Obtén la dirección IP del clúster con el siguiente comando:
```plain
kubectl get svc -l istio=ingressgateway -n istio-system
```{{exec}}

Si intentas conectarte a la aplicación utilizando `curl` a la dirección IP del clúster, notarás que no recibirás ninguna respuesta de la aplicación.
```plain
CLUSTER_IP=$(kubectl get svc -l istio=ingressgateway -n istio-system -o jsonpath='{.items[0].spec.clusterIP}')
curl http://$CLUSTER_IP
```{{exec}}

Esto se debe a que aún falta un paso adicional para finalizar la configuración de Istio: crear el **Virtual Service**.

Para continuar presiona el botón **NEXT**
