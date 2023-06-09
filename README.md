Prometheus is SUPPOSED TO BE used for capturing, "scraping" and storing data, though it's still capable of executing
PromQL statements. It requires EXPORTERS to actually export that data.

Exporters can vary a lot, there are HTTP exporters which fetch HTTP related data from prometheus, hardware-oriented exporters
which get data about firewalls, memory, CPU usage, etc. 
Go here to check out various exporters prometheus supports and can be integrated with: 
https://prometheus.io/docs/instrumenting/exporters/

node-exporter is used to export hardware and OS metrics exposed by *NIX kernels.
For windows, we use windows exporter.

In context of this lesson, we're using cAdvisor (Container Advisor) Exporter which is used to export data of containers.
https://github.com/google/cadvisor

cAdvisor:
    - dev by google
    - cAdvisor works at host's kernel level and gather metrics regarding containers
    - can measure strain containers apply on host and stuff

Now, see. Docker on Windows runs inside a Hyper-V (tech used to virtualize stuff in Windows) MobyLinux VM.
So we can still reference a Linux based directory system in our docker-compose files, we just have to run one commmand:
``` 
$Env:COMPOSE_CONVERT_WINDOWS_PATHS=1 
```
This environment variable is used by Docker Compose to automatically convert file paths from Windows-style to Unix-style 
when running Docker containers on Windows. 

Yet to work on promql