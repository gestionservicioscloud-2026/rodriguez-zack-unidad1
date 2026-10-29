# Instructivo para el alumno: creación y uso de tu repositorio de proyecto

Este instructivo te acompaña durante toda la unidad. Léelo antes de crear tu repositorio y vuelve a él cada vez que trabajes en el proyecto. Todo lo que aquí se pide está directamente relacionado con la **Rúbrica de evaluación vía GitHub**: si sigues estos pasos, cumples con los criterios de evaluación.

> **Importante:** vas a usar **un solo repositorio por unidad**, no uno distinto por cada tarea o taller. Cada tarea vive dentro de ese repositorio, en su propia carpeta.

---

## Paso 1 — Crea tu repositorio a partir de la plantilla

**1.1** Entra a: <https://github.com/gestionservicioscloud-2026/plantilla-proyecto-gestionservicioscloud>

**1.2** Haz clic en el botón verde **"Use this template"** → **"Create a new repository"**.

> No hagas *fork* ni clones directamente la plantilla: "Use this template" crea una copia limpia, sin el historial de commits de la plantilla, para que tu progreso incremental se vea desde tu primer commit.

**1.3 Paso crítico — Owner del repositorio.**
En la pantalla de creación verás un campo **"Owner"** con un menú desplegable (por defecto muestra tu usuario personal). Debes cambiarlo a:

```
gestionservicioscloud-2026
```

> ⚠️ No dejes tu usuario personal seleccionado. Si el repositorio queda bajo tu cuenta personal en lugar de la organización del curso, no podrá ser encontrado ni evaluado, y tendrás que rehacer este paso.
>
> Si la organización no aparece en el menú, todavía no aceptaste la invitación: revisa tu correo o entra a <https://github.com/orgs/gestionservicioscloud-2026/invitation>.

**1.4** Nombra tu repositorio exactamente con este formato (todo en minúsculas, con guiones, sin espacios ni tildes):

```
apellido-nombre-unidad[n]
```

Ejemplo real para la Unidad 1: `perez-juan-unidad1`

> No agregues palabras extra al nombre (ni "uide", ni "gestioncloud", ni ningún otro texto): el nombre debe verse exactamente así, sin variaciones.

**1.5** En visibilidad, selecciona **Public** (no privado), para que pueda ser revisado.

**1.6** Haz clic en **"Create repository"**.

> Este mismo repositorio va a recibir todas las tareas y talleres de la unidad. No crees uno nuevo para cada entrega.

**Verifica que quedó bien:** la URL de tu repositorio debe verse así:

```
https://github.com/gestionservicioscloud-2026/apellido-nombre-unidad1
```

Si en cambio dice `github.com/tu-usuario-personal/...`, algo salió mal en el paso 1.3. Corrígelo antes de seguir: **Settings → Danger Zone → Transfer ownership** → escribe `gestionservicioscloud-2026`.

---

## Paso 2 — Clónalo a tu computadora

Copia la URL exacta de tu propio repositorio (la de la organización, verificada en el paso anterior) y reemplázala aquí:

```bash
git clone https://github.com/gestionservicioscloud-2026/apellido-nombre-unidad1.git
cd apellido-nombre-unidad1
```

Ejemplo real para Juan Pérez, Unidad 1:

```bash
git clone https://github.com/gestionservicioscloud-2026/perez-juan-unidad1.git
cd perez-juan-unidad1
```

> Si no tienes Git instalado o prefieres no usar la terminal, puedes trabajar directamente desde **GitHub Codespaces** (botón **"Code"** → **"Codespaces"** → **"Create codespace"**) sin instalar nada. El codespace ya trae Go, Git y la CLI de AWS.

---

## Paso 3 — Haz tu primer commit: completa la portada

1. Abre `README.md` y completa la tabla **Datos del estudiante**.
2. Guarda y sube el cambio:

```bash
git add README.md
git commit -m "docs: completa datos del estudiante"
git push
```

Este primer commit marca el inicio de tu trabajo en la unidad.

---

## Paso 4 — Trabaja cada tarea en su propia carpeta

Para cada tarea o taller:

1. **Copia la carpeta modelo** `tarea-00-ejemplo` y renómbrala con el número y un nombre corto, en minúsculas y con guiones:

   ```bash
   cp -r tarea-00-ejemplo tarea-01-registro-aws-academy
   ```

   Ejemplos de nombres válidos: `tarea-01-registro-aws-academy`, `taller-01-redes-ssh`, `tarea-02-vpc-subredes`.

2. **Completa el `README.md` de la carpeta**: objetivo, pasos realizados, evidencias y reflexión.
3. **Guarda las capturas** en la subcarpeta `evidencias/` con nombres descriptivos (`01-conexion-ssh.png`, `02-free-h.png`).
4. **Agrega la fila** de la entrega en la tabla **Entregas de la unidad** del `README.md` principal.

### Commits pequeños y frecuentes

La rúbrica valora el **progreso incremental**: varios commits a lo largo del tiempo, no uno solo el día de la entrega. Haz un commit cada vez que termines una parte:

```bash
git add tarea-01-registro-aws-academy
git commit -m "tarea-01: agrega captura del laboratorio iniciado"
git push
```

Usa mensajes que expliquen **qué** hiciste. Formato sugerido: `carpeta: qué hiciste`.

| ✅ Buen mensaje | ❌ Mal mensaje |
| --- | --- |
| `tarea-02: documenta bloque CIDR de la VPC` | `cambios` |
| `taller-01: agrega salida de ss -tuln` | `asdf` |
| `docs: actualiza índice de entregas` | `final final ahora sí` |

---

## Paso 5 — Nunca subas secretos

Trabajamos con servidores y cuentas en la nube. **Nunca** subas al repositorio:

- Contraseñas, llaves privadas (`.pem`, `id_rsa`) o tokens.
- Credenciales de AWS (`aws_access_key_id`, `aws_secret_access_key`) ni archivos `.env`.

El archivo `.gitignore` de la plantilla ya bloquea los casos más comunes, pero revisa siempre con `git status` qué vas a subir antes de hacer commit. Si subiste un secreto por error, avisa de inmediato a tu docente: borrar el archivo después **no** lo elimina del historial.

---

## Paso 6 — Antes de cada fecha de entrega

- [ ] La URL de mi repositorio empieza con `github.com/gestionservicioscloud-2026/`.
- [ ] El nombre del repositorio es `apellido-nombre-unidad[n]`, sin palabras extra.
- [ ] La tabla **Datos del estudiante** está completa.
- [ ] Cada entrega está en su propia carpeta, con su `README.md` y sus evidencias.
- [ ] El índice de entregas del `README.md` principal está actualizado.
- [ ] Hice varios commits a lo largo del trabajo, con mensajes claros.
- [ ] Hice `git push` y veo mis últimos cambios en GitHub.
- [ ] La revisión automática (pestaña **Actions**) aparece en verde ✅.

> La pestaña **Actions** de tu repositorio ejecuta una revisión automática en cada `push`: comprueba el nombre del repositorio, que la portada esté completa y que cada carpeta de entrega tenga su `README.md`. Si aparece en rojo ❌, abre el detalle: el mensaje te dice qué corregir.
