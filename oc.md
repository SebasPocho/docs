## Ver BC:
```
oc get bc
```

## Ver Builds:
```
oc get builds
```

## Borrar Builds:
```
oc delete build $(oc get build|grep "Failed\|Cancelled")
oc delete build $(oc get build|grep "Failed\|Cancelled\|Pending\|New")
```

## Borrar pods:
```
oc delete pod $(oc get pod|grep "Error\|CreateContainerConfigError\|CrashLoopBackOff\|Completed" | awk '{print $1}')

for p in $(oc get pods | grep "Error\|CreateContainerConfigError\|CrashLoopBackOff\|Completed" | awk '{print $1}'); do oc delete pod $p --grace-period=0 --force;done
```

## create Secret:
```
apiVersion: v1
kind: Secret
metadata:
  name: sql
type: Opaque
stringData:
  PASSWORD: nueva12345
  USER:  dhbrm01m
  ```
  
## delete pod:
```
oc delete pod  <podname> --grace-period=0 --force
```


## limits:
```
oc edit limits limits
```

## route timeout:
```
oc annotate route <routename> --overwrite haproxy.router.openshift.io/timeout=300s
```

## mount secret en pv:
```
oc set volume dc/case-query --add -t secret --secret-name=secret-certificate -m /opt/certificate
```

## unmount secret en pv:
```
oc set volumes dc/consultasolicituddynamics --remove=true --mount-path='/opt/keystore' --confirm

oc set volumes dc/apisdesk  --remove=true --name='appd-agent-repo' --confirm

```

## Copiar logs desde pod:
```
oc rsync offer-command-17-7sm2m:/tmp/appd/dotnet/1_agent_0.log /devops/shorton/logsAppd/
```

## Instalar Jaeger:
```
oc new-app jaegertracing/all-in-one:1.20.0 --name=jaegertracing-all-in-one -n <namespace> && oc expose svc jaegertracing-all-in-one --port=16686 -n <namespace> 
oc new-app jaegertracing/all-in-one:1.20.0 --name=jaegertracing-all-in-one -n devo-devops-dev && oc expose svc jaegertracing-all-in-one --port=16686 -n devo-devops-dev
```

## Flush Redis:
```
1. redis-cli
2. auth yourpassword
3. FLUSHDB command – Delete all the keys of the currently selected DB.
   FLUSHALL command – Delete all the keys of all the existing databases, not
```

## Fecha Creación proyectos:
```
oc get projects -o custom-columns=NAME:.metadata.name,CREATED:.metadata.creationTimestamp
```

## Secrets tipo keystore:
```
oc create secret generic keystore --from-file=keystore.jks=keystore.jks --type=opaque

oc set volume dc/consultasolicitud --add -t secret --secret-name=keystore -m /opt/keystore

```
## Rsync a pod:
```
oc rsync --progress=true <from> <podname>:<ruta en el pod>
oc rsync --progress=true staticdevops/ onb-cdn-web-5-n9tc7:/opt/app-root/etc/nginx.d/devopsmaster

oc rsync --progress=true <podname>:<ruta en el pod> <to> 
oc rsync odretriever-16-vqqlv:/opt/ibm/odwek/V10.5/www/api/ODApi.jar /devops/shorton/odwekjar/ 
```

## Top pods:
```
oc adm top pods | grep "cap-impersonal-auth-controller-v2-40*"
```
