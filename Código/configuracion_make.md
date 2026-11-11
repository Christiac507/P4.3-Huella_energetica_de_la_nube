# Configuración del escenario en Make: `Huella_Nube_Equipo#`

Flujo: **Página web → Webhook de Make → Make AI Agent → Webhook Response → Página web**

## Módulos

| # | Módulo | Configuración |
|---|--------|---------------|
| 1 | Webhooks → Custom webhook | Crear uno nuevo, copiar la URL y pegarla en `WEBHOOK_URL` de `index.html`. Con *Run once* llenar la página con datos de prueba y presionar **Calcular mi huella**: deben aparecer los 8 campos (`video`, `musica`, `redes`, `videollamadas`, `juegos`, `nube`, `ia`, `correos`). |
| 2 | Make AI Agent | Connection: Make's AI Provider (créditos del plan Pro, sin API key). Input y Instructions: ver abajo. |
| 3 | Webhooks → Webhook Response | Status `200`. Body: respuesta del AI Agent. Headers: `Content-Type` = `text/plain; charset=utf-8` y `Access-Control-Allow-Origin` = `*`. |

Guardar y activar el escenario con **Immediately as data arrives**.

> Sin el header `Access-Control-Allow-Origin` el navegador rechaza la respuesta de Make y la página muestra el mensaje de error.

## Input del AI Agent

Mapear cada campo desde el panel (no escribir los números de módulo a mano):

```
Video: {{1.video}} h/dia
Musica: {{1.musica}} h/dia
Redes sociales: {{1.redes}} h/dia
Videollamadas: {{1.videollamadas}} h/semana
Juegos en linea: {{1.juegos}} h/dia
Nube: {{1.nube}} GB guardados
IA: {{1.ia}} consultas al dia
Correos: {{1.correos}} al dia
```

## Instructions del AI Agent

```
Eres un analista de sustentabilidad digital para alumnos de Desarrollo Sustentable del TecNM.
Recibiras el uso digital de una persona. Estima la energia que ese uso provoca en centros de datos y redes.
Reglas:
- Usa este factor de emision: 0.444 kg CO2e por kWh (fuente: SEMARNAT, factor de emision del Sistema Electrico Nacional 2024, publicado en 2025).
- Para cada actividad indica el valor de kWh por hora (o por unidad) que supones. Si las fuentes varian mucho, usa un valor intermedio y dilo.
- No presentes las estimaciones como datos exactos.
Responde en texto plano (sin asteriscos, sin markdown), en espanol, con este formato:

ENERGIA ESTIMADA
Por semana: [kWh]
Por año: [kWh]
Emisiones por año: [kg CO2e]
Equivale a: [kilometros en auto o dias con un foco LED encendido]

SUPOSICIONES
[una linea por actividad con el valor usado]

¿QUIEN PAGA ESTE COSTO?
[3 lineas: por que es una externalidad, que recursos consume (energia, agua) y quien la absorbe]

3 ACCIONES PARA REDUCIRLA
1. [...]
2. [...]
3. [...]
```
