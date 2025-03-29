# utn-devops
grupo1-repo-devops

Se ha optado por un sitio web estático, ver mas detalles [aquí](https://github.com/kity-linuxero/devops-web-actividad1).

## Requerimientos
- [Vagrant](https://developer.hashicorp.com/vagrant/install?product_intent=vagrant)
- [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
- [Git](https://git-scm.com/downloads) (opcional)

## Instrucciones

#### 1) Luego de instaladas las dependencias, preparar el directorio de trabajo:

```bash
mkdir grupo1-devops
cd grupo1-devops
```

#### 2) Descargar los repositorios:

```bash
# Directorio que contiene la aplicación
git clone https://github.com/kity-linuxero/devops-web-actividad1.git

# Directorio que contiene el Vagrantfile para aprovisionamiento
git clone https://github.com/kity-linuxero/utn-devops.git
```
Si no se tiene git instalado, puede descargarlos desde:

- [SitioWeb](https://github.com/kity-linuxero/devops-web-actividad1/archive/refs/heads/main.zip)
- [utp-devops repo](https://github.com/kity-linuxero/utn-devops/archive/refs/heads/main.zip)

> [!IMPORTANT]  
> Si ha optado por descargar desde la URL a los repositorio debe primero descomprimir los archivos.


#### 3) Cambiar de directorio 
```bash
cd utn-devops
```

#### 4) Cambiar al branch correspondiente
```bash
git switch unidad-1-vagrant
```

La estructura de directorios debe quedar de la siguiente manera:

```
grupo1-devops/
├─ devops-web-actividad1/
│  ├─ index.html
├─ utn-devops/
│  ├─ nginx-config/
│  │  ├─ nginx-default
│  ├─ Vagrantfile
```


#### 5) Ejecutar el siguiente comando para aprovisionar la VM con Vagrant:

```bash
vagrant up
```

#### 6) Una vez finalizado el comando, abrimos VirtualBox y debería verse así

![](./img/virtualbox.png)

#### 7) Abrir el navegador para verificar

- Abrir [localhost:8080](http://localhost:8080)
- Si todo va bien debería verse así:

![](./img/web_sreenshot.png)

Si algo no funciona, puede intentar con

```bash
vagrant reload
```

#### 8) Detener VM mediante comandos de Vagrant

```bash
vagrant halt
```

Si se desea eliminar la VM

```bash
vagrant destroy
```


