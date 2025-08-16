
### 1) Configurar Git por primera vez
```bash
git --version

# Identidad de tus commits
git config --global user.name "Tu Nombre"
git config --global user.email "tu-email@ejemplo.com"


# Rama por defecto “main”
git config --global init.defaultBranch main

# Saltos de línea recomendados
# Windows:
git config --global core.autocrlf true

# (Opcional) VS Code como editor para mensajes de commit
git config --global core.editor "code --wait"

# Ver configuración
git config --global --list
```




### 2) Bajar un repositorio (clonar)
```bash
# HTTPS
git clone https://github.com/USUARIO/REPO.git
cd REPO

# o SSH (si tienes clave en GitHub)
git clone git@github.com:USUARIO/REPO.git
cd REPO
```




### 3) Subir información al repo (agregar, commitear, empujar)
```bash
git status
git add .                         # añade cambios
git commit -m "Descripción"       # crea el commit
git push -u origin main           # primera vez en la rama main
# luego solo: git push
```




### 4) Traer actualizaciones de GitHub (no tienes cambios locales)
```bash
git checkout main
git fetch origin
git pull --ff-only origin main     # actualiza sin crear merges innecesarios
```




### 5) Yo cambié cosas y en GitHub también: subir sin romper (rebase)
```bash
git add . && git commit -m "Mi cambio"   # guarda tus cambios

git fetch origin
git pull --rebase origin main            # pone tus commits encima de lo nuevo
# si hay conflictos: edita archivos (<<<<<<< ======= >>>>>>>)
git add <archivos_resueltos>
git rebase --continue                    # repite hasta terminar

git push                                  # sube tus commits rebaseados
```




###  Variante: aún no quiero commitear (stash)
```bash
git stash push -m "WIP local"
git pull --rebase origin main
git stash pop
# si aparecen conflictos → resuélvelos y sigue
```




### 6) Autenticación para git push
HTTPS: usa un Personal Access Token como “contraseña”.
SSH (recomendado):
```bash
ssh-keygen -t ed25519 -C "tu-email@ejemplo.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub    # pega esto en GitHub → Settings → SSH and GPG keys
# Cambiar remoto a SSH:
git remote set-url origin git@github.com:USUARIO/REPO.git
```



### 7) Comandos útiles
```bash
git status
git log --oneline --graph --decorate -n 10
git branch -vv
git remote -v
git restore --staged <fichero>     # quitar de "staged"
git checkout -- <fichero>          # descartar cambios en un fichero (¡cuidado!)
```



### 8) Igualarme EXACTO al remoto (descarta local) ⚠️
```bash
git fetch origin
git reset --hard origin/main
```




### 9) ¿Por qué mi prompt muestra (main) en ~?
Porque hiciste git init en tu carpeta HOME. Solución:
```bash
cd ~
rm -rf .git       # elimina solo el seguimiento Git del HOME
```
Trabaja siempre dentro de la carpeta del repo clonado (por ejemplo ~/Projects/REPO).


### 10) Agregar, commitear y subir los cambios al repositorio
```bash
git status
git add README.md
git commit -m "Corrijo bloques de código a bash en README"
git push
```



### Consejo: activa el rebase por defecto para un flujo más limpio:
```bash
git config --global pull.rebase true
```
Si te aparece algún error concreto al hacer pull/push, copia el mensaje y ajustamos el comando exacto.

