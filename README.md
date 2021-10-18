# Resource Partition APIs

## Suppose the Resource Partition Server is running on ubuntu machine having IP 192.168.1.243 so these will be available APIs

### 1. APIs for Nodes on RP server:

  *	API to GET node list on Resource Partition Server: -

````bigquery
http://192.168.1.243:8080/api/v1/nodes
````                 
  * API to GET a specific node on Resource Partition Server: -
````bigquery
http://192.168.1.240:8080/api/v1/nodes/{node-name}
````

### 2. APIs for Services on RP server:

  * API to GET Services list on Resource Partition Server: -
````bigquery
http://192.168.1.243:8080/api/v1/services
````
  * 2.	API to GET a specific Service on Resource Partition Server: -	
````bigquery
http://192.168.1.243:8080/api/v1/namespaces/{namespace-name}/services/{service-name}
````
  * API to CREATE Service on Resource Partition Server: -
````bigquery
http://192.168.1.243:8080/api/v1/namespaces/{namespace-name}/services
````
#### Note: Here is an example of nginx-service.yaml where one can have to pass
####       the name of the service in value of ‘name’ key (for example here service name is “nginx-service”)
####       the name of the namespace in value of ‘namespace’ key (for example here namespace name is “default”)

````bigquery
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
  tenant: system
  namespace: default
  labels: 
    app: nginx
spec:
  type: ClusterIP
  ports:
  - name: http
    port: 80
    protocol: TCP
    targetPort: 80
  selector:
    app: nginx
````

  * API to CREATE  a Service under specific tenant on Resource Partition Server: -
````bigquery
http://192.168.1.243:8080/api/v1/tenants/{tenant-name}/namespaces/{namespace-name}/services
````
#### Note: Here is an example of nginx-service.yaml where one can have to pass
####       the name of the service in value of ‘name’ key (for example here service name is “nginx-service”)
####       the name of the tenant in value of ‘tenant’ key (for example here tenant name is “tenant-1”)
####       the name of the namespace in value of ‘namespace’ key (for example here namespace name is “default”)
````bigquery
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
  tenant: tenant-1
  namespace: default
  labels: 
    app: nginx
spec:
  type: ClusterIP
  ports:
  - name: http
    port: 80
    protocol: TCP
    targetPort: 80
  selector:
    app: nginx
````
  * API to DELETE a Service  on Resource Partition Server: -
````bigquery
http://192.168.1.243:8080/api/v1/namespaces/{namespace-name}/services/{service-name}
````

  * API to DELETE a Service under specific tenant on Resource Partition Server: -  
````bigquey
 http://192.168.1.243:8080/api/v1/tenants/{tenant-name}namespaces/{namespace-name}/services/{service-name}
````
  
### 3. APIs for Service Accounts: -

  * API to GET Service Accounts list on Resource Partition Server: -	                   
```bigquery
http://192.168.1.243:8080/api/v1/serviceaccounts
````

  * API to GET a specific Service Account  on Resource Partition Server: -	      
````bigquery
http://192.168.1.243:8080/api/v1/namespaces/{namespace-name}/serviceaccounts/{sa-name}
````

  * API to CREATE Service Account  on Resource Partition Server: -	                   
````bigquery
http://192.168.1.243:8080/api/v1/serviceaccounts
````
#### Note: The referal yaml can like below where one can have to pass
####       the name of the service account in value of ‘name’ key (for example here service name is “test-service-account”)
####       the name of the namespace in value of ‘namespace’ key (for example here namespace name is “kube-system”)
````bigquery
apiVersion: v1
kind: ServiceAccount
  metadata:
    name: test-service-account
    tenant: system
    namespace: kube-system
````

  * API to CREATE Service Account under specific tenant on Resource Partition Server: -	                   
````bigquery
http://192.168.1.243:8080/api/v1/tenants/{tenant-name}/namespaces/{namespace-name}/serviceaccounts
````
#### Note: The referal yaml can like below where one can have to pass
####       the name of service account in value of ‘name’ key (for example here service name is “test-service-account”)
####       the name of the tenant in value of ‘tenant’ key (for example here tenant is “tenant-2”).
####       the name of the namespace in value of ‘namespace’ key (for example here namespace name is “namespace-2”)

````bigquery
apiVersion: v1
kind: ServiceAccount
  metadata:
    name: test-service-account
    tenant: tenant-2
    namespace: namespace-2
````

  * API to DELETE Service Account  on Resource Partition Server: -	                   
````bigquery
http://192.168.1.243:8080/api/v1/namespaces/{namespace-name}/serviceaccounts/{serviceaccount-name}
````

  * API to DELETE a Service Account under specific tenant on Resource Partition Server: -  
````bigquery
http://192.168.1.243:8080/api/v1/tenants/{tenant-name}/namespaces/{namespace-name}/serviceaccounts/{sa-name}
````

### 4. APIs for Namespaces:-

  * API to GET namespaces  list on Resource Partition Server: -
````bigquery
http://192.168.1.243:8080/api/v1/namespaces/ 
````

  * API to GET a specific namespace on Resource Partition Server: -
````bigquery
http://192.168.1.243:8080/api/v1/namespaces/{namespace-name}
````

  * API to CREATE namespaces on Resource Partition Server: -
````bigquery
http://192.168.1.243:8080/api/v1/namespaces/
````

#### Note: The referal yaml can like below where one can have to pass
####       the name of the namespace in value of ‘name’ key (for example here name of namespace is “test-namespace”)

```bigquery
apiVersion: v1
kind: Namespace
  metadata:
    name: test-namespace
    tenant: system
````

  * API to CREATE a namespace under a specific tenant on Resource Partition Server: -
````bigquery
http://192.168.1.243:8080/api/v1/tenants/{tenant-name}/namespaces
````
#### Note: The referal yaml can like below where one can have to pass
####       the name of the namespace in value of ‘name’ key (for example here name of namespace is “namespace-2”)
####       the name of the tenant in value of ‘tenant’ key (for example here tenant name is “tenant-2”)

````bigquery
apiVersion: v1
kind: Namespace
metadata: 
  name: namespace-2
  tenant: tenant-2
````

  * API to DELETE namespaces on Resource Partition Server: -
````bigquery
http://192.168.1.243:8080/api/v1/namespaces/{namespace-name}
````

  * API to DELETE a namespace under specific tenant on Resource Partition Server: -	
````bigquery
http://192.168.1.243:8080/api/v1/tenants/{tenant-name}/namespaces/{namespace-name}
````

### 5. APIs for DaemonSets: -

  * API to GET daemon sets  list on Resource Partition Server: -
````bigquery
http://192.168.1.243:8080/apis/apps/v1/daemonsets/
````

### 6. APIs for Tenants: - 

  * API to GET tenant  list on Resource Partition Server: -
````bigquery 
http://192.168.1.243:8080/api/v1/tenants
````
  * API to GET a specific tenant on Resource Partition Server: -
````bigquery
http://192.168.1.243:8080/api/v1/tenants/{tenant -name}
````

  * API to CREATE tenant  on Resource Partition Server: -
````bigquery
http://192.168.1.243:8080/api/v1/tenants
````

#### Note: The referal yaml can like below where one can have to pass
####       the name of the tenant in value of ‘tenant’ key (for example here tenant name is “tenant-4”)

````bigquery
apiVersion: v1
kind: Tenant
metadata:
  name: tenant-4
spec:
  storageClusterId: 0
````

  * API to DELETE a tenant on Resource Partition Server: -
````bigquery
http://192.168.1.243:8080/api/v1/tenants/{tenant-name}
````
