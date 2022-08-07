## Habilitar la inyección automática del Sidecar

Ejecuta el siguiente comando para habilitar la inyección automática del Sidecar Envoy en el namespace `default`

```plain
kubectl label namespace default istio-injection=enabled --overwrite
```{{exec}}

Para continuar presiona el botón NEXT
