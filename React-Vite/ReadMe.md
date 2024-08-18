To build docker image of your app by the name "my-vite-app"
you can alway change "my-vite-app" which your docker image name

```bash
docker build -t my-vite-app .
```

To run docker "my-vite-app" and map host and docker port

```bash
docker run -p 5173:5173 my-vite-app
```

