# WorldApp Harness

WorldApp Harness es un agente de programacion con IA para la terminal, configurado por defecto para usar la API de World App Technologies.

## Proveedor De IA Predeterminado

WorldApp usa la API compatible con OpenAI de World App Technologies.

- URL base: `https://platform.worldapptechnologies.com/api/v1`
- Modelo principal: `world-app-technologies-api/nulu-4.8`
- Modelo rapido: `world-app-technologies-api/nulu-4.8-flash`

Los usuarios solo necesitan una clave de API de World App Technologies.

```bash
export WORLDAPP_API_KEY="sk_wat_your_key"
```

## Instalar Desde El Codigo Fuente

```bash
git clone https://github.com/jinxlo/Worldapp-harness.git
cd Worldapp-harness
bun install --ignore-scripts
cd packages/opencode
bun run build --single --skip-install
./dist/worldapp-linux-x64/bin/worldapp --help
```

## Ejecutar

```bash
worldapp
```

O ejecuta una solicitud de una sola vez:

```bash
worldapp run "Review this project"
```

## Configuracion

La configuracion del proyecto se carga desde `worldapp.json`, `worldapp.jsonc` y directorios `.worldapp/`.

Ejemplo para sobrescribir el proveedor:

```json
{
  "provider": {
    "world-app-technologies-api": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "World App Technologies API",
      "options": {
        "baseURL": "https://platform.worldapptechnologies.com/api/v1",
        "apiKey": "{env:WORLDAPP_API_KEY}"
      },
      "models": {
        "nulu-4.8": {},
        "nulu-4.8-flash": {}
      }
    }
  },
  "model": "world-app-technologies-api/nulu-4.8",
  "small_model": "world-app-technologies-api/nulu-4.8-flash",
  "enabled_providers": ["world-app-technologies-api"]
}
```

## Desarrollo

```bash
cd packages/opencode
bun typecheck
bun run build --single --skip-install
```

## Licencia

Este proyecto se distribuye bajo la licencia MIT. Consulta `LICENSE` para ver el aviso de copyright upstream requerido.
