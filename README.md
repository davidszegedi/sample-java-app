This repo contains two similars applications built using Quarkus and Spring runtimes.
The goal is to perform simple tests and compare behavior between the two runtimes.

Simply use: 

```# kubectl apply -f quarkus-petclinic/manifests/quarkus-petclinic.yaml```

and

# kubectl apply -f spring-petclinic/manifests/spring-petclinic.yaml

in order to deploy applications within their dedicated namespaces.

You can generate basic load by executing mutiple isntances of curl, for instance: 

# while true; do curl -H "Cache-Control: no-cache, no-store, must-revalidate" -H "Pragma: no-cache" -H "Expires: 0" quarkus-petclinic-service.quarkus-petclinic.svc.cluster.local:8080/owners?lastName= ; done

# while true; do curl -H "Cache-Control: no-cache, no-store, must-revalidate" -H "Pragma: no-cache" -H "Expires: 0" spring-petclinic-service.spring-petclinic.svc.cluster.local:8080/owners?lastName= ; done

from as many clients as needed, as far as they have direct access to the service, the idea being to keep traffic local to the cluster and avoid ingress usage.
