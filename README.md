# Generador de Actividades · ESPA Canarias

Herramienta para docentes de la Educación Secundaria para Personas Adultas (ESPA) en Canarias.

Permite seleccionar criterios de evaluación de los **3 ámbitos** (Científico-Tecnológico, Comunicación y Social) y generar actividades didácticas con IA.

## Arquitectura

- **Frontend**: HTML estático vanilla (index.html)
- **Backend**: Vercel Serverless Function (api/generate.js) que hace de proxy a Groq
- **API Key**: Almacenada como variable de entorno en Vercel — nunca expuesta al frontend

```
index.html          → Interfaz del selector + generador
api/generate.js     → Proxy serverless a Groq (streaming)
vercel.json         → Configuración de Vercel
```

## Despliegue en Vercel

1. Sube este directorio a un repo de GitHub
2. En [vercel.com](https://vercel.com): Import Project → selecciona el repo
3. En **Settings > Environment Variables**, añade:
   - `GROQ_API_KEY` = `tu_clave_de_groq`
4. Deploy

## Modelos disponibles (Groq)

- Llama 3.3 70B Versatile
- Llama 4 Scout 17B
- Llama 3.1 8B Instant
- Gemma 2 9B
- Mixtral 8x7B
- Compound Beta (agentic)

## Datos curriculares

Extraídos del Anexo IV del Currículo de la ESPA (Consejería de Educación de Canarias):

- **ACT** (Ámbito Científico-Tecnológico): 9 competencias específicas, 22 criterios
- **ACO** (Ámbito de Comunicación): 9 competencias específicas, 28 criterios
- **ASO** (Ámbito Social): 10 competencias específicas, 36 criterios

**Total: 86 criterios de evaluación**
