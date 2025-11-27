# ⚡️astro-bento-portfolio

## A personal portfolio website made using `Astro`.

![astro-bento-portfolio | Bento-like Personal Porfolio Template](public/preview.png)

# Steps ▶️

```bash
# Clone this repository
$ git clone https://github.com/MarioProjects/bento_personal_website
```

```bash
# Go into the repository
$ cd bento_personal_website
```

```bash
# Install dependencies
$ pnpm install
or
$ npm install
```

```bash
# Start the project in development
$ pnpm run dev
or
$ npm run dev
```


# Configuration

remember to replace the `site` and other properties with your data in `astro.config.mjs`

# Deploy

We are using Docker to deploy the project, so you need to have Docker installed on your machine.

```bash
# Build the image
docker build -t bento-personal-site:latest .
docker run -d -p 9001:8080 --name bento-personal-site bento-personal-site
```

### Configuración de Deployment Automático

Estando ya dentro del servidor, lo más fácil es generar un par de llaves nuevo **específico para GitHub Actions**. Esto es más seguro que usar tus llaves personales.

Sigue estos pasos en tu terminal del servidor:

1.  **Genera las llaves** (dale a Enter a todo para dejarlas sin contraseña, GitHub Actions no soporta llaves con contraseña fácilmente):

    ```bash
    ssh-keygen -t ed25519 -C "github-actions" -f ~/.ssh/github_deploy_key
    ```

2.  **Autoriza la llave pública** para que permita el acceso:

    ```bash
    cat ~/.ssh/github_deploy_key.pub >> ~/.ssh/authorized_keys
    ```

3.  **Obtén la llave PRIVADA** (esta es la que necesitas copiar):

    ```bash
    cat ~/.ssh/github_deploy_key
    ```

Copia **todo** el bloque de texto que salga, incluyendo `-----BEGIN OPENSSH PRIVATE KEY-----` y `-----END OPENSSH PRIVATE KEY-----`. Ese bloque de texto es lo que debes pegar en el secreto `SERVER_SSH_KEY` en GitHub.

### Ejecutar el despliegue

El deployment se activa automáticamente al subir un tag que comience con `v` (ejemplo: `v1.0.0`).

1. **Crear un tag** con la nueva versión:

   ```bash
   git tag v1.0.0
   ```

2. **Subir el tag** a GitHub:

   ```bash
   git push origin v1.0.0
   ```

Esto disparará el workflow de GitHub Actions que construye la imagen Docker y la despliega en el servidor.

# Info

To modify the **light/dark** theme, you need to go to the `src/styles/global.css` file and modify the `:root` properties.

## Acknowledgements

- Gianmarco - https://github.com/Ladvace
- Dark Theme - https://www.tohuwabohu.io/2022/11/astrojs-theme-toggle
