# daw
Documentación en curso

# clase 1

- Crear una cuenta en github
- Crear un nuevo repositorio: daw
- instalar git
- Si aparece un error "no se pudo bloquear /var/lib/dpkg/lock" ..., introducir la siguiente instrucción:

```
sudo fuser -vki /var/lib/dpkg/lock
```

y volver a instalar git.

```
sudo apt install git
```

### Instrucciones básicas git
- Clonar el repositorio remoto
```
git clone url
```

- Ver estado del repositorio local
```
git status
```

- Hacer un "commit" (comprometer) los cambios al repositorio local
```
git commit -am "mensaje"
```

- Subir (push) los cambios del repositorio local al repositorio remoto:
```
git push origin master
```

- Actualizar (pull) el repositorio local con los cambios desde el repositorio remoto
```
git pull origin master
```

### Añadir clave ssh a github

En primer lugar instalamos openssh-server:
```
sudo apt install openssh-server
```

Después generamos una clave:
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
Una vez generada la clave, la copiamos al portapapeles. Para ello, mostramos la clave por la consola del sistema, y luego la copiamos:
```
cat ~/.ssh/id_rsa.pub
```
y la añadimos a github (settings -> SSH and PGP keys)

Arrancamos el agente "ssh" en segundo plano:
```
eval "$(ssh-agent -s)"
```

y ahora añadimos la clave al agente:
```
ssh-add ~/.ssh/id_rsa
```

Para que github acepte la conexión ssh hay que modificar la direccion "origin". Para ver la dirección actual:
```
git remote show origin
```

Esto nos mostrará un mensaje similar a este:
```
URL  para obtener: https://github.com/calaespi/daw.git
URL para publicar: https://github.com/calaespi/daw.git
```

Ahora hay que modificar esta dirección añadiendo la opcion "ssh":
```
git remote set-url origin git+ssh://git@github.com/calaespi/daw.git
```