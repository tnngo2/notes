# Best practice for writing Dockerfiles

Write a better Dockerfiles means:
- incremental build time
- image size
- maintainability
- security and repeatability

## Incremental build time

Development cycle
- build a Docker image
- make code changes
- rebuilding   

🌟 important to use caching

### Tip #1: Order matters

![](images/2019-08-22-14-11-47.png)

Order steps from least to most frequently changing steps to optimize caching.

❓ Why?  
A step's cache is invalidated by changing files or modifying lines in the Dockerfile

### Tip #2: More specific COPY
![](images/2019-08-22-14-14-05.png)

❓ Why  
Any changes to the files being copied will break the cache

### Tip #3: Identify cachable units such as apt-get update & install
![](images/2019-08-22-14-16-04.png)

❓ Why   
When installing packages from package managers, always should update the index and install packages at the same RUN because they form as a cachable unit.
Otherwise you risk installing outdated packages.

## Reduce image size

Smaller images equal faster deployments and a smaller attach surface.

### Tip #4: Remove unncessary dependencies
![](images/2019-08-22-14-19-55.png)
- Remove unncessary dependencies, do not install debugging tools.
- Add --no-install-recommends flag to ensures unnecessary dependencies not installed.

### Tip #5: Remove package manager cache
- Package managers maintain their own cache which may end up in the image, so you should remove the cache in the same RUN instruction that installed package. Removing it in another RUN instruction would not reduce the image size.

![](images/2019-08-22-14-22-26.png)

## Maintainability
### Tip #6: Use official images when possible
- Official images save time spent on maintainance because all the installation are done and best practices are applied.
![](images/2019-08-22-14-26-50.png)

### Tip #7: Use specific tags
- Do not use the latest tag because the breaking changes will happen over time.
- If you rebuild the Dockerfile without cache, you may have failing builds
![](images/2019-08-22-14-28-01.png)

### Tip #8: Look for