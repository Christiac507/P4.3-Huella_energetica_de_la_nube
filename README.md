# Práctica 4.3 – Huella energética de la nube

**Instituto Tecnológico de Mazatlán** · Ingeniería en Sistemas Computacionales
**Asignatura:** Desarrollo Sustentable (ACD-0908) · **Unidad 4:** Escenario económico
**Tema:** 4.3 Externalización e internalización de costos
**Alumno:** Christian Paul Lizárraga Oronia
**Profesor:** Miguel Ángel Barrón Hernández

---

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
| `Código/` | `index.html` (la calculadora), `Huella_Nube_Equipo#.blueprint.json` (blueprint exportado de Make) y `configuracion_make.md` (módulos e instrucciones de la IA) |
| `Imágenes/` | Capturas del escenario, del tiempo de pantalla y de los resultados |
| `Video/` | `enlace.txt` con el enlace al video en YouTube |
| `Resultados/` | Informe en PDF con investigación, resultados y preguntas |

## Resultados

Datos reales del celular (Bienestar digital, viernes 6 de noviembre) y de la cuenta de Google:

| Actividad | Valor |
|-----------|-------|
| Video en streaming (TikTok) | 1.9 h/día |
| Redes sociales (Instagram + WhatsApp) | 1.9 h/día |
| Música, videollamadas, juegos | 0 |
| Nube | 14.55 GB |
| Consultas a IA | 6 al día |
| Correos | 0 al día |

**Estimación del agente de IA:** 146.82 kWh por año y 65.17 kg CO₂e por año (≈ 540 km en auto). La actividad que más consume es el video en streaming (≈ 69 kWh/año, 47 %).

**Verificación:** la IA supuso 0.1 kWh por hora de video, que está dentro del rango de las fuentes (0.077 – 0.188 kWh). El total anual es correcto, pero el valor por semana que dio (3.41 kWh) no: con sus propias suposiciones son 2.82 kWh.

El informe completo está en [`Resultados/`](Resultados/).

## Preguntas de reflexión

**1. ¿Por qué el consumo de energía de la nube es una externalidad? ¿Quién la paga realmente?**

Es una externalidad porque cuando vemos videos, usamos redes sociales o le preguntamos algo a una IA, el precio que pagamos (muchas veces cero, o solo la suscripción) no incluye el daño ambiental de la electricidad y el agua que consumen los centros de datos y las redes. Esa electricidad en México se genera en buena parte con gas natural y combustóleo, lo que libera CO₂ y otros contaminantes. Los centros de datos además usan grandes cantidades de agua para enfriar sus equipos, muchas veces en zonas con escasez. El costo lo pagan las comunidades que viven cerca de las centrales eléctricas y de los centros de datos, la sociedad en general a través del cambio climático, y las generaciones futuras, no la empresa ni el usuario.

**2. ¿Qué actividad digital genera más consumo en su equipo y por qué?**

En nuestro caso, la actividad que más consume es el video en streaming, que en mi caso es TikTok, con unos 69 kWh por año, el 47 % del total según la estimación. El video es normalmente la actividad que más energía gasta porque transmite muchos datos por segundo y obliga a la pantalla y al router a estar encendidos durante horas. Además, es la actividad a la que más tiempo dedicamos al día, entre TikTok, YouTube y series. En comparación, un correo o una consulta a la IA gastan poca energía de forma individual, aunque las consultas a IA consumen más que una búsqueda normal porque requieren procesadores especiales en el centro de datos.

**3. ¿Qué tan confiable es la estimación de la IA? ¿Qué suposición cambiaría más el resultado?**

La estimación es útil para darse una idea del orden de magnitud, pero no es un dato exacto. La IA elige valores de kWh por hora que pueden variar mucho según la fuente: para el video, la IEA estima unos 0.077 kWh y Carbon Trust unos 0.188 kWh, más del doble. En nuestro resultado la IA usó 0.1 kWh por hora de video, que sí está dentro de ese rango. Además, al revisar sus cuentas encontramos que el total por año era correcto, pero el valor por semana (3.41 kWh) no: con sus propias suposiciones salen 2.82 kWh. La suposición que más cambia el resultado es la energía por hora de video, porque es la actividad con más horas; también influye si se cuenta o no el dispositivo y el router de la casa. Por eso la IA debe explicar sus suposiciones y nosotros compararlas con fuentes confiables.

**4. ¿Cómo podría internalizarse este costo (impuestos, energía renovable en centros de datos, precios distintos)?**

Una forma es aplicar un impuesto al carbono a la electricidad que consumen los centros de datos, para que las empresas paguen por sus emisiones y les convenga ahorrar energía. Otra es obligar a que los nuevos centros de datos usen energía renovable (solar o eólica) y reporten su consumo de agua, como ya se discute en Europa. También podrían ofrecerse precios distintos: planes más baratos para quien vea video en calidad estándar o descargue contenido en lugar de verlo varias veces en streaming. Finalmente, etiquetas que muestren el consumo de energía de cada servicio ayudarían a que el usuario conozca el costo real y elija mejor.

**5. ¿Qué cambio en su uso digital están dispuestos a hacer?**

Mi mayor consumo está en TikTok e Instagram, que juntas suman casi 4 horas al día. Estoy dispuesto a bajar una hora diaria entre las dos, sobre todo en la noche, y a usar el modo de ahorro de datos para que los videos se reproduzcan en menor calidad. También voy a limpiar mi almacenamiento en la nube, que está casi lleno (14.55 de 15 GB): borrar fotos repetidas de Google Fotos y reducir la copia de seguridad de WhatsApp (5 GB), quitando videos y audios que ya no necesito. Para medir si funciona, revisaré mi tiempo de pantalla cada semana y volveré a calcular mi huella en un mes.
