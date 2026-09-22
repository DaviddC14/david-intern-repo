# What is Docker and Why Use It? Reflection

**How does Docker differ from a virtual machine?**
A Virtual Machine (VM) virtualizes the physical hardware, meaning each VM runs a complete, heavy Guest Operating System on top of a Hypervisor. Docker, on the other hand, virtualizes the Operating System. Containers share the host machine's OS kernel, making them significantly more lightweight, faster to boot up (in seconds rather than minutes), and less resource-intensive than traditional VMs.

**Why is containerization useful for a backend like Focus Bear's?**
Focus Bear relies on a complex architecture (NestJS API, PostgreSQL, Redis, background jobs). Containerization ensures that this entire ecosystem can be spun up reliably anywhere. It guarantees absolute consistency across local development machines, testing environments, and production servers, completely eliminating the notorious "it works on my machine" excuse.

**How do containers help with dependency management?**
Containers package the application code alongside all of its required dependencies, libraries, and runtime environments (like a specific version of Node.js or Alpine Linux) into a single, immutable image. This means developers don't need to manually install or configure global dependencies on their host machines; everything the app needs to run is isolated inside the container.

**What are the potential downsides of using Docker?**
While powerful, Docker adds an extra layer of abstraction which comes with a learning curve, especially regarding networking and volume management. Additionally, because Docker runs natively only on Linux, running it on macOS or Windows requires a lightweight background VM (like WSL2 on Windows), which can sometimes consume high amounts of RAM or cause file-system syncing delays during local development.