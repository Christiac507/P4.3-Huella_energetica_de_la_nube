# Práctica 4.3 – Huella energética de la nube

**Instituto Tecnológico de Mazatlán** · Ingeniería en Sistemas Computacionales
**Asignatura:** Desarrollo Sustentable (ACD-0908) · **Unidad 4:** Escenario económico
**Tema:** 4.3 Externalización e internalización de costos
**Alumno:** Christian Paul Lizárraga Oronia
**Profesor:** Miguel Ángel Barrón Hernández

---

## 🎥 Video

[▶ Ver el video de la práctica en YouTube](https://www.youtube.com/watch?v=PEGA_AQUI_EL_ID_DEL_VIDEO)

## 🌐 Página publicada

[Abrir la calculadora en GitHub Pages](https://christiac507.github.io/P4.3-Huella_energetica_de_la_nube/C%C3%B3digo/)

---

## Objetivo

Reconocer el consumo energético de los servicios digitales como un costo externalizado, estimar la huella digital propia con apoyo de IA y evaluar críticamente las suposiciones de esa estimación.

## ¿Cómo funciona?

```
Página web (index.html)
   │  POST con URLSearchParams (8 campos)
   ▼
Webhook de Make → Make AI Agent → Webhook Response
   │
   ▼
La página muestra: energía estimada, emisiones, suposiciones,
quién paga el costo y 3 acciones para reducirlo
```

1. La persona captura su uso digital (datos reales del tiempo de pantalla del celular).
2. Make recibe los 8 campos y el Make AI Agent estima kWh y kg CO₂e con el factor de emisión del Sistema Eléctrico Nacional (**0.444 kg CO₂e/kWh**, SEMARNAT).
3. La respuesta regresa como texto plano y se muestra en la página.

## Campos que captura la página

| Campo | Qué mide |
|-------|----------|
| video | Horas al día de video en streaming |
| musica | Horas al día de música en streaming |
| redes | Horas al día en redes sociales |
| videollamadas | Horas a la semana de videollamadas |
| juegos | Horas al día de juegos en línea |
| nube | GB guardados en la nube |
| ia | Consultas al día a chatbots de IA |
| correos | Correos enviados al día |

## Tecnologías

- HTML, CSS y JavaScript (un solo archivo, sin librerías externas)
- Make: Webhooks, Make AI Agent, Webhook Response
- GitHub Pages

## Estructura del repositorio

| Carpeta | Contenido |
|---------|-----------|
| `Código/` | `index.html` (la calculadora) y `configuracion_make.md` (módulos e instrucciones de la IA) |
| `Imágenes/` | Capturas del escenario, del tiempo de pantalla y de los resultados |
| `Video/` | Video de la práctica (enlace arriba) |
| `Resultados/` | Informe en PDF con investigación, resultados y preguntas |

## Resultados

La tabla con los kWh y kg CO₂e por año, la verificación de la suposición de la IA para el video en streaming y las respuestas a las preguntas están en [`Resultados/`](Resultados/).
