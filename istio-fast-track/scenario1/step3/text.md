## Desplegar la aplicación web

Utiliza el editor de Killercoda para visualizar el archivo `istio-fast-track/istiol-lab1/hello-world-deployment.yml` y observa el contenido del archivo.

El archivo `hello-world-deployment.yml` creará:
* Un pod hello-world que expondrá el puerto 3000
* Un servicio hello-world que expondrá el puerto 80

![Explorer](https://github.com/Ivan-Ferreira-GH/killercoda/blob/main/istio-fast-track/scenario1/step3/explorer-hello-world.deployment.png?raw=true "Explorer")

Para aplicar la configuración ejecuta el siguiente comando:

```plain
kubectl apply -f ~/istio-fast-track/istio-lab1/yml/hello-world-deployment.yml
```{{exec}}

Verifica que el pod ha sido desplegado y observa la cantidad de imágenes que existen en el pod a través de la columna `READY`.
```plain
k get po -o wide
```{{exec}}

Como has activado la inyección automática del *Sidecar* de Istio, deberías visualizar 2/2 en la columna `READY`:
```
NAME                          READY   STATUS    RESTARTS   AGE    IP            NODE     NOMINATED NODE   READINESS GATES
hello-world-977c594d4-f6qlp   2/2     Running   0          5m7s   192.168.1.9   node01   <none>           <none>
```

Para continuar presiona el botón **NEXT**
