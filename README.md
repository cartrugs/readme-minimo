# README mínimo necesario de documentación para que cualquiera pueda empezar con sus propios medios

![PHP](https://shields.io/badge/-PHP-3776AB?style=flat&logo=php)

![Laravel](https://img.shields.io/badge/Laravel-10-red)

[![Vue.js](https://img.shields.io/badge/Vue.js-4FC08D?logo=vuedotjs&logoColor=fff)](#)


![Logo de readme][imagen1]

[imagen1]: ./assets/l1N10XpkhNLh0ars7Xcf7FHVkhs.svg

## Índice

- [Mínimo indispensable](#1-mínimo-indispensable-debería-estar-siempre-sin-exagerar)
  - [Descripción general del proyecto](#a-descripción-general-del-proyecto-por-breve-que-sea)
  - [Tecnologías principales](#b-tecnologías-principales)
  - [Requisitos previos](#c-requisitos-previos)
  - [Instrucciones básicas de instalación](#d-instrucciones-básicas-de-instalación)
- [Nivel estándar de documentación](#2-nivel-estándar-de-documentación-muy-recomendable)
  - [Estructura general](#a-estructura-general)
  - [Flujo funcional (breve)](#b-flujo-funcional-breve)
- [Nivel opcional](#nivel-opcional-pero-muy-recomendable)
  - [Lista de endpoints o rutas API](#a-lista-de-endpoints-o-rutas-api)
  - [Variables de entorno en .env](#b-variables-de-entorno-en-env)
  
---

## 1. Mínimo indispensable (debería estar siempre, sin exagerar)

Estos puntos garantizan que alguien pueda **entender qué hace el proyecto y cómo ponerlo en marcha sin tener que ir a tirones.**

### a) Descripción general del proyecto (por breve que sea)

Un párrafo corto que responda al menos a:

- ¿Qué hace el sistema?
- ¿Cuál es su propósito principal (por lo menos una descripción breve )?
- ¿A quién va dirigido o qué problema resuelve?

Ejemplo:

```markdown
Este programa gestiona la generación, firma digital y almacenamiento de pólizas en formato PDF para su posterior envío y archivo usando (PICK y NAS).
```

---

### b) Tecnologías principales

Al menos mencionar el **stack base**, por ejemplo:

```markdown
- Backend: Laravel 10 (PHP 8.2)
- Frontend: Vue.js 3 + Vite
- Base de datos: D3
- Almacenamiento: NAS corporativo + Storage Laravel
- Firma digital: API de Signaturit
```

---

### c) Requisitos previos

Breve lista de dependencias del entorno:

```markdown
- PHP >= 8.2
- Composer
- Node.js >= 18
- D3
- Extensiones PHP: zip, mbstring, fileinfo, etc.
- wkhtmltopdf
```

---

### d) Instrucciones básicas de instalación

El clásico 'cómo levantarlo localmente':

```bash
git clone https://...
composer install
npm install
cp .env.example .env 
php artisan key:generate
php artisan migrate --seed
npm run dev ## Arrancar front
php artisan serve ## Arrancar el back
```

Con esto, ya cualquiera puede arrancarlo (NO PROBLEMA 😎)

[Volver al índice](#índice)

---

## 2. Nivel estándar de documentación (muy recomendable)

Pensado para proyectos colaborativos o de cierta complejidad, pero recomendable de cualquier manera.

### a) Estructura general

Un resumen de módulos o capas (para visualizar la forma de trabajar):

```markdown
/app/Http/Controllers → Controladores principales (Polizas, Calidad, etc.)
app/Services → Lógica de negocios (PDF, NAAS, Signaturit, etc)
app/Traits → Funciones compartidas (manejo de usuarios, logs)
resources/js/components → Frontend Vue (formularios y vistas)
```

---

### b) Flujo funcional (breve)

Una descripción vaga pero necesaria del flujo general:

> Resumen del flujo principal (de las generación a la descarga de la póliza)

```markdown
1. El usuario selecciona pólizas para generar.
2. El backend genera los PDFs con...
3. Se agrupa y se comprime en un ZIP.
4. Se registran en PICK mediante PolizaRepository
5. Los usuarios pueden descargar las pólizas firmadas desde el NAS.
```

Aporta al menos el **contexto mínimo de cómo se relacionan los módulos** sin entrar directamente en el código.

[Volver al índice](#índice)

---

## Nivel opcional (pero muy recomendable)

### a) Lista de endpoints o rutas API

Lo ideal sería una lista o tabla:

| **Endpoint** | **Método** | **Descripción** |
| ------------ | ---------- | --------------- |
| `/api/polizas/massive-generate` | POST | Genera y descarga ZIP con pólizas seleccionadas |
| `/api/polizas/reception` | POST | Consulta y descarga pólizas firmadas desde Signaturit |
| `/api/polizas/download` | GET | Descarga se documentos desde NAS |

---

### b) Variables de entorno en .env

Al menos las principales claves que necesita:

```ini
SIGNATURIT_APY_KEY= 
NAS_PAT=/mnt/nas/polizas
PICK_API_URL=https://...
```

[Volver al índice](#índice)

---
