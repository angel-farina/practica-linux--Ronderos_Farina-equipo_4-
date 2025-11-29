# Errores Encontrados y Solucionados

## Error 1: Red inconsistente en redis
**Problema:** El servicio redis usaba `monitoring-network` mientras otros usaban `monitoring`
**Comando para identificar:** `docker-compose config`
**Solucion:** Cambiar a `monitoring` para mantener consistencia

## Error 2: Nombre de volumen inconsistente
**Problema:** Grafana usaba `grafana-data` pero el volumen se declaro como `grafana-storage`
**Comando para identificar:** `docker-compose config` y `docker-compose logs grafana`
**Solucion:** Unificar el nombre a `grafana-storage` (o viceversa)

## Error 3: Target de Prometheus
**Problema:** Nginx no expone metricas en el puerto 9113 por defecto
**Comando para identificar:** Acceder a http://localhost:9090/targets
**Solucion:** Comentar el job de nginx en prometheus.yml
**Explicacion:** Nginx alpine no incluye nginx-prometheus-exporter
