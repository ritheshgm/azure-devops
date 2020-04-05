# A Sample Vert.x Microservice
This simple service was developed to demonstrate the following:

- capture all project-related files in Bitbucket
    - source code
    - build scripts
    - configurations
    - Jenkins pipeline script
    - Docker image files
    - Helm chart files
    - code analysis
    - tests
- automatically build project in Jenkins after push to Bitbucket
    - build jar file
    - scan jar file for bugs
    - build docker image
    - build helm chart
    - deploy docker image and helm chart to Harbor
    - test microservice in Kubernetes sandbox
    - if tests pass, then publish helm chart to public catalog

## Implementation
This microservice is implemented as a jar file deployed as a docker container.  The
microservice feeds the following static web pages from the URL and port assigned
by kubernetes:

- url:port/index.html
- url:port/page1.html
- url:port/page2.html
- url:port/page3.html

The index page implements cache controls that should force the page to be refreshed
automatically by the browser when an update is published, but if you don't see the 
desired results simply refresh the browser page.