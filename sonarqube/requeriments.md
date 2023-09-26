# Sonarqube

## Requerimientos

### Elasticsearch

Para que elasticsearch se inicie de manera óptima, se deben pasar algunas comprobaciones de arranque. La búsqueda elástica requiere este aumento en la memoria virtual, ya que internamente elasticsearch utiliza mapas de memoria o mmapfs para almacenar archivos para los que requiere memoria virtual.

**Verificar el valor actual**

```shell
sudo sysctl vm.max_map_count
```

Cambiar el valor temporalmente

```shell
sysctl -w vm.max_map_count=262144
```

**Cambiar de forma permanente**

Para aplicar los cambios de forma permanente debe actualizar el archivo sysctl.conf (/etc/sysctl.conf o /etc/sysctl.d/99-sysctl.conf) y agregar la siguiente línea.

```shell
vm.max_map_count=262144
```

Esto funcionará sólo cuando reiniciemos el servidor. Para establecer el valor sin reiniciar el servidor, también puede usar el siguiente comando. Este comando cargará los valores del archivo.

```shell
sudo sysctl -p
# O
sudo sysctl --system 
```
