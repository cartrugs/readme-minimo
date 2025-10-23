# README mínimo necesario de documentación para que cualquiera pueda empezar con sus propios medios

![][imagen1]

[imagen1]: ./assets/l1N10XpkhNLh0ars7Xcf7FHVkhs.svg

## Índice

- [Mínimo indispensable](#1-mínimo-indispensable-debería-estar-siempre-sin-exagerar)
- [Nivel estándar de documentación](#2-nivel-estándar-de-documentación-muy-recomendable)
- [Nivel opcional](#nivel-opcional-pero-muy-recomendable)

## 1. Mínimo indispensable (debería estar siempre, sin exagerar)

Estos puntos garantizan que alguien pueda **entender qué hace el proyecto y cómo ponerlo en marcha sin tener que ir a tirones.**

**a) Descripción general del proyecto (por breve que sea)**

Un parráfo corto que responda al menos a:

- ¿Qué hace el sistema?
- ¿Cuál es su propósito principal (por lo menos una descripción breve )?
- ¿A quién va dirigido o qué problema resuelve?

Ejemplo:
```bash
Este programa gestiona la generación, firma digital y almacenamiento de pólizas en formato PDF para su posterior envío y archivo usando (PICK y NAS).
```

---

**b) Tecnologías principales**

Al menos mencionar el **stack base**, por ejemplo:

```diff
- Backend: Laravel 10 (PHP 8.2)
- Frontend: Vue.js 3 + Vite
- Base de datos: D3
- Almacenamiento: NAS coorporativo + Storage Laravel
- Firma digital: API de Signaturit
```

---

**c) Requisitos previos**

Breve lista de dependencias del entorno:

```diff
- PHP >= 8.2
- Composer
- Node.js >= 18
- D3
- Extensiones PHP: zip, mbstring, fileinfo, etc.
- wkhtmltopdf
```

---

**d) Instrucciones básicas de instalación**

El clásico 'cómo levantarlo localmente':

```bash
git clone https://...
composer install
npm install
cp .env.example .env 
php artisan key:generate
php artisan migrate --seed
npm run dev ## Arrancar front
php artisan serve ## Arranacar el back
```

Con esto, ya cualquiera puede arrancarlo (NO PROBLEMA 😎)

---

## 2. Nivel estándar de documentación (muy recomendable)

Pensado para proyectos colaborativos o de cierta complejidad, pero recomendable de cualquier manera.

**a) Estructura general del sistema**

Un resumen de módulos o capas (para visualizar la forma de trabajar):
```bash
/app/Http/Controllers → Controladores principales (Polizas, Calidad, etc.)
app/Services → Lógica de negocios (PDF, NAAS, Signaturit, etc)
app/Traits → Funciones compartidas (manejo de usuarios, logs)
resources/js/components → Frontend Vue (formularios y vistas)
```

---

**b) Flujo funcional (breve)**

Una descripción vaga pero necesaria del flujo general:

```markdown
1. El usuario selecciona pólizas para generar.
2. El backend genera los PDFs con...
3. Se agrupa y se comprime en un ZIP.
4. Se registran en PICK mediante PolizaRepository
5. Los usuarios pueden descargar las pólizas firmadas desde el NAS.
```

Aporta al menos el **contexto mínimo de cómo se relacionan los módulos** sin entrar directamente en el código.

---

## Nivel opcional (pero muy recomendable)

**a) Lista de endpoints o rutas API**

Lo ideal sería una lista o tabla:

| **Endpoint** | **Método** | **Descripción** |
| ------------ | ---------- | --------------- |
| `/api/polizas/massive-generate` | POST | Genera y descarga ZIP con pólizas seleccionadas |
| `/api/polizas/reception` | POST | Consulta y descarga pólizas firmadas desde Signaturit |
| `/api/polizas/download` | GET | Descarga se documentos desde NAS |

---

**b) Variables de entorno en .env**

Al menmos las principales claves que necesita:

```ini
SIGNATURIT_APY_KEY= 
NAS_PAT=/mnt/nas/polizas
PICK_API_URL=https://...
```

---



