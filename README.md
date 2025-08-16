## CConfigurar Git por primera vez


git --version

# Identidad de tus commits
git config --global user.name "Tu Nombre"
git config --global user.email "tu-email@ejemplo.com"
# (Opcional) Correo privado de GitHub:
# 12345678+tuusuario@users.noreply.github.com

# Rama por defecto “main”
git config --global init.defaultBranch main

# Saltos de línea recomendados
# Windows:
git config --global core.autocrlf true
# macOS/Linux:
# git config --global core.autocrlf input

# (Opcional) VS Code como editor para mensajes de commit
git config --global core.editor "code --wait"

# Ver configuración
git config --global --list
