
## Create versioning git hook

Para conectar los hooks de git con los commits y recrear una version progresiva automaticamentes, ejecute los siguientes comandos:

```
sudo nano .git/hooks/pre-commit
```

agregue el siguiente contenido al archivo:

```
#!/bin/sh
# To enable this hook, rename this file to "pre-commit".

git log develop --pretty=oneline | wc -l > version
git add version

major_version="3"
minor_version=`cat version`

echo "v$major_version.$minor_version" > version

git add .

```
agregue permisons de ejecucion al archivo 

```
sudo chmod +x pre-commit
```

Guarde

```
sudo git add .
sudo git commit -m <yourtag>
cat version (debería poder ver la versión en consola)
git push 
```
NOTA: Para cambiar la version MAJOR:

```
sudo nano .git/hooks/pre-commit
```
Cambie el valor de la variable major_version="3"
Guarde
