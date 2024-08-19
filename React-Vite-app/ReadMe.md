
1. **Build the Docker Image**

   ```bash
   docker build -t my-vite-app .
   ```

   - **Purpose**: Builds a Docker image from your Dockerfile and tags it with the name `my-vite-app`. You can change `my-vite-app` to any other name you prefer.

2. **Run the Docker Container (Port Mapping)**

   ```bash
   docker run -p 5173:5173 my-vite-app
   ```

   - **Purpose**: Runs the container from the `my-vite-app` image and maps port 5173 on the host to port 5173 in the container. This setup allows you to access your app at `http://localhost:5173`.
   - **Note**: Changes made to files on the host will not be reflected inside the container with this command.

3. **Run the Docker Container (Port Mapping with Volume Mounting and Node Module Isolation)**

   ```bash
   docker run -it -p 5173:5173 -v "$(pwd):/app" -v /app/node_modules my-vite-app
   ```

   - **Purpose**: 
     - `-it`: Runs the container in interactive mode with a TTY attached, allowing you to interact with the container’s process.
     - `-p 5173:5173`: Maps port 5173 on the host to port 5173 in the container.
     - `-v "$(pwd):/app"`: Mounts the current working directory on the host (`$(pwd)`) to `/app` in the container. This makes your local project files available inside the container.
     - `-v /app/node_modules`: Creates a named volume for `/app/node_modules`, isolating the container’s `node_modules` from any potential conflicts with the host’s `node_modules`. This ensures that the container uses its own dependencies.
   - **Note**: This setup reflects real-time changes made to your local files inside the container and prevents conflicts between host and container dependencies.
