# n8n - Dev Image

Dockerfile which allows to package up the local n8n code into
a docker image.


## Usage

Execute the following in the n8n root folder:
```bash
docker build -t n8n-dev -f docker/images/n8n-dev/Dockerfile .
docker run -it -p 5678:5678 -p 8080:8080 -v $(pwd):/home/node/n8n n8n-dev
```

## Development

```bash
cd /home/node/n8n
lerna bootstrap --hoist
npm run build
npm run dev
```
