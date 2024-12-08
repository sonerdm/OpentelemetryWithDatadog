# W3C Trace Context Example
This project consists of two Flask servers and one Express server instrumented with Opentelemetry on a standalone host.

## Start the Demo
1. Create .env file under the rolldice-game directory.
2. Add DD_SITE and DATADOG_API_KEY environments in .env file.
3. Run docker-compose up

To trigger the service call

### Success
```bash
curl -X POST http://localhost:5002/play_game \
     -H "Content-Type: application/json" \
     -d '{"player": "John Doe"}'
```
### Error
``` bash
curl -X POST http://localhost:5002/play_game \
     -H "Content-Type: application/json" \
     -d '{}'
```
View traces & standalone host in app.datadoghq.eu
PS: Domain could be different based on your Datadog account region.