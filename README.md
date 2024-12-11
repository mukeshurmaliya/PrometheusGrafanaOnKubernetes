# PrometheusGrafanaOnKubernetes
Setup Prometheus and Grafana on Kubernetes Instance and then monitor Kubernetes Resources

mukeshurmaliya@MASK ~ % helm
The Kubernetes package manager

Common actions for Helm:

- helm search:    search for charts
- helm pull:      download a chart to your local directory to view
- helm install:   upload the chart to Kubernetes
- helm list:      list releases of charts

Environment variables:

| Name                               | Description                                                                                                |
|------------------------------------|------------------------------------------------------------------------------------------------------------|
| $HELM_CACHE_HOME                   | set an alternative location for storing cached files.                                                      |
| $HELM_CONFIG_HOME                  | set an alternative location for storing Helm configuration.                                                |
| $HELM_DATA_HOME                    | set an alternative location for storing Helm data.                                                         |
| $HELM_DEBUG                        | indicate whether or not Helm is running in Debug mode                                                      |
| $HELM_DRIVER                       | set the backend storage driver. Values are: configmap, secret, memory, sql.                                |
| $HELM_DRIVER_SQL_CONNECTION_STRING | set the connection string the SQL storage driver should use.                                               |
| $HELM_MAX_HISTORY                  | set the maximum number of helm release history.                                                            |
| $HELM_NAMESPACE                    | set the namespace used for the helm operations.                                                            |
| $HELM_NO_PLUGINS                   | disable plugins. Set HELM_NO_PLUGINS=1 to disable plugins.                                                 |
| $HELM_PLUGINS                      | set the path to the plugins directory                                                                      |
| $HELM_REGISTRY_CONFIG              | set the path to the registry config file.                                                                  |
| $HELM_REPOSITORY_CACHE             | set the path to the repository cache directory                                                             |
| $HELM_REPOSITORY_CONFIG            | set the path to the repositories file.                                                                     |
| $KUBECONFIG                        | set an alternative Kubernetes configuration file (default "~/.kube/config")                                |
| $HELM_KUBEAPISERVER                | set the Kubernetes API Server Endpoint for authentication                                                  |
| $HELM_KUBECAFILE                   | set the Kubernetes certificate authority file.                                                             |
| $HELM_KUBEASGROUPS                 | set the Groups to use for impersonation using a comma-separated list.                                      |
| $HELM_KUBEASUSER                   | set the Username to impersonate for the operation.                                                         |
| $HELM_KUBECONTEXT                  | set the name of the kubeconfig context.                                                                    |
| $HELM_KUBETOKEN                    | set the Bearer KubeToken used for authentication.                                                          |
| $HELM_KUBEINSECURE_SKIP_TLS_VERIFY | indicate if the Kubernetes API server's certificate validation should be skipped (insecure)                |
| $HELM_KUBETLS_SERVER_NAME          | set the server name used to validate the Kubernetes API server certificate                                 |
| $HELM_BURST_LIMIT                  | set the default burst limit in the case the server contains many CRDs (default 100, -1 to disable)         |
| $HELM_QPS                          | set the Queries Per Second in cases where a high number of calls exceed the option for higher burst values |

Helm stores cache, configuration, and data based on the following configuration order:

- If a HELM_*_HOME environment variable is set, it will be used
- Otherwise, on systems supporting the XDG base directory specification, the XDG variables will be used
- When no other location is set a default location will be used based on the operating system

By default, the default directories depend on the Operating System. The defaults are listed below:

| Operating System | Cache Path                | Configuration Path             | Data Path               |
|------------------|---------------------------|--------------------------------|-------------------------|
| Linux            | $HOME/.cache/helm         | $HOME/.config/helm             | $HOME/.local/share/helm |
| macOS            | $HOME/Library/Caches/helm | $HOME/Library/Preferences/helm | $HOME/Library/helm      |
| Windows          | %TEMP%\helm               | %APPDATA%\helm                 | %APPDATA%\helm          |

Usage:
  helm [command]

Available Commands:
  completion  generate autocompletion scripts for the specified shell
  create      create a new chart with the given name
  dependency  manage a chart's dependencies
  env         helm client environment information
  get         download extended information of a named release
  help        Help about any command
  history     fetch release history
  install     install a chart
  lint        examine a chart for possible issues
  list        list releases
  package     package a chart directory into a chart archive
  plugin      install, list, or uninstall Helm plugins
  pull        download a chart from a repository and (optionally) unpack it in local directory
  push        push a chart to remote
  registry    login to or logout from a registry
  repo        add, list, remove, update, and index chart repositories
  rollback    roll back a release to a previous revision
  search      search for a keyword in charts
  show        show information of a chart
  status      display the status of the named release
  template    locally render templates
  test        run tests for a release
  uninstall   uninstall a release
  upgrade     upgrade a release
  verify      verify that a chart at the given path has been signed and is valid
  version     print the client version information

Flags:
      --burst-limit int                 client-side default throttling limit (default 100)
      --debug                           enable verbose output
  -h, --help                            help for helm
      --kube-apiserver string           the address and the port for the Kubernetes API server
      --kube-as-group stringArray       group to impersonate for the operation, this flag can be repeated to specify multiple groups.
      --kube-as-user string             username to impersonate for the operation
      --kube-ca-file string             the certificate authority file for the Kubernetes API server connection
      --kube-context string             name of the kubeconfig context to use
      --kube-insecure-skip-tls-verify   if true, the Kubernetes API server's certificate will not be checked for validity. This will make your HTTPS connections insecure
      --kube-tls-server-name string     server name to use for Kubernetes API server certificate validation. If it is not provided, the hostname used to contact the server is used
      --kube-token string               bearer token used for authentication
      --kubeconfig string               path to the kubeconfig file
  -n, --namespace string                namespace scope for this request
      --qps float32                     queries per second used when communicating with the Kubernetes API, not including bursting
      --registry-config string          path to the registry config file (default "/Users/mukeshurmaliya/Library/Preferences/helm/registry/config.json")
      --repository-cache string         path to the directory containing cached repository indexes (default "/Users/mukeshurmaliya/Library/Caches/helm/repository")
      --repository-config string        path to the file containing repository names and URLs (default "/Users/mukeshurmaliya/Library/Preferences/helm/repositories.yaml")

Use "helm [command] --help" for more information about a command.
mukeshurmaliya@MASK ~ % minikube
minikube provisions and manages local Kubernetes clusters optimized for development workflows.

Basic Commands:
  start            Starts a local Kubernetes cluster
  status           Gets the status of a local Kubernetes cluster
  stop             Stops a running local Kubernetes cluster
  delete           Deletes a local Kubernetes cluster
  dashboard        Access the Kubernetes dashboard running within the minikube cluster
  pause            pause Kubernetes
  unpause          unpause Kubernetes

Images Commands:
  docker-env       Provides instructions to point your terminal's docker-cli to the Docker Engine inside minikube.
(Useful for building docker images directly inside minikube)
  podman-env       Configure environment to use minikube's Podman service
  cache            Manage cache for images
  image            Manage images

Configuration and Management Commands:
  addons           Enable or disable a minikube addon
  config           Modify persistent configuration values
  profile          Get or list the current profiles (clusters)
  update-context   Update kubeconfig in case of an IP or port change

Networking and Connectivity Commands:
  service          Returns a URL to connect to a service
  tunnel           Connect to LoadBalancer services

Advanced Commands:
  mount            Mounts the specified directory into minikube
  ssh              Log into the minikube environment (for debugging)
  kubectl          Run a kubectl binary matching the cluster version
  node             Add, remove, or list additional nodes
  cp               Copy the specified file into minikube

Troubleshooting Commands:
  ssh-key          Retrieve the ssh identity key path of the specified node
  ssh-host         Retrieve the ssh host key of the specified node
  ip               Retrieves the IP address of the specified node
  logs             Returns logs to debug a local Kubernetes cluster
  update-check     Print current and latest version number
  version          Print the version of minikube
  options          Show a list of global command-line options (applies to all commands).

Other Commands:
  completion       Generate command completion for a shell
  license          Outputs the licenses of dependencies to a directory

Use "minikube <command> --help" for more information about a given command.
mukeshurmaliya@MASK ~ % minikube start 
😄  minikube v1.34.0 on Darwin 13.7.1
🆕  Kubernetes 1.31.0 is now available. If you would like to upgrade, specify: --kubernetes-version=v1.31.0
✨  Using the hyperkit driver based on existing profile
💿  Downloading VM boot image ...
    > minikube-v1.34.0-amd64.iso....:  65 B / 65 B [---------] 100.00% ? p/s 0s
    > minikube-v1.34.0-amd64.iso:  333.55 MiB / 333.55 MiB  100.00% 39.77 MiB p
👍  Starting "minikube" primary control-plane node in "minikube" cluster
🔄  Restarting existing hyperkit VM for "minikube" ...
❗  Image was not built for the current minikube version. To resolve this you can delete and recreate your minikube cluster using the latest images. Expected minikube version: v1.33.1 -> Actual minikube version: v1.34.0
🐳  Preparing Kubernetes v1.30.0 on Docker 26.0.2 ...
🔗  Configuring bridge CNI (Container Networking Interface) ...
🔎  Verifying Kubernetes components...
    ▪ Using image gcr.io/k8s-minikube/storage-provisioner:v5
🌟  Enabled addons: storage-provisioner, default-storageclass
🏄  Done! kubectl is now configured to use "minikube" cluster and "default" namespace by default
mukeshurmaliya@MASK ~ % kubectl get pods
NAME                         READY   STATUS    RESTARTS      AGE
mynginxws-84b5485f7c-lvg7n   1/1     Running   2 (69s ago)   17d
mukeshurmaliya@MASK ~ % kubectl get nodes
NAME       STATUS   ROLES           AGE    VERSION
minikube   Ready    control-plane   205d   v1.30.0
mukeshurmaliya@MASK ~ % helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
"prometheus-community" has been added to your repositories
mukeshurmaliya@MASK ~ % helm search repo prometh
NAME                                              	CHART VERSION	APP VERSION	DESCRIPTION                                       
bitnami/kube-prometheus                           	10.0.4       	0.78.1     	Prometheus Operator provides easy monitoring de...
bitnami/prometheus                                	1.3.28       	2.55.1     	Prometheus is an open source monitoring and ale...
bitnami/wavefront-prometheus-storage-adapter      	2.3.3        	1.0.7      	DEPRECATED Wavefront Storage Adapter is a Prome...
prometheus-community/kube-prometheus-stack        	66.3.1       	v0.78.2    	kube-prometheus-stack collects Kubernetes manif...
prometheus-community/prometheus                   	26.0.0       	v3.0.0     	Prometheus is a monitoring system and time seri...
prometheus-community/prometheus-adapter           	4.11.0       	v0.12.0    	A Helm chart for k8s prometheus adapter           
prometheus-community/prometheus-blackbox-exporter 	9.1.0        	v0.25.0    	Prometheus Blackbox Exporter                      
prometheus-community/prometheus-cloudwatch-expo...	0.26.0       	0.16.0     	A Helm chart for prometheus cloudwatch-exporter   
prometheus-community/prometheus-conntrack-stats...	0.5.13       	v0.4.21    	A Helm chart for conntrack-stats-exporter         
prometheus-community/prometheus-consul-exporter   	1.0.0        	0.4.0      	A Helm chart for the Prometheus Consul Exporter   
prometheus-community/prometheus-couchdb-exporter  	1.0.0        	1.0        	A Helm chart to export the metrics from couchdb...
prometheus-community/prometheus-druid-exporter    	1.1.0        	v0.11.0    	Druid exporter to monitor druid metrics with Pr...
prometheus-community/prometheus-elasticsearch-e...	6.5.1        	v1.8.0     	Elasticsearch stats exporter for Prometheus       
prometheus-community/prometheus-fastly-exporter   	0.5.0        	v9.0.0     	A Helm chart for the Prometheus Fastly Exporter   
prometheus-community/prometheus-ipmi-exporter     	0.5.0        	v1.9.0     	This is an IPMI exporter for Prometheus.          
prometheus-community/prometheus-json-exporter     	0.14.0       	v0.6.0     	Install prometheus-json-exporter                  
prometheus-community/prometheus-kafka-exporter    	2.11.0       	v1.8.0     	A Helm chart to export the metrics from Kafka i...
prometheus-community/prometheus-memcached-exporter	0.4.0        	v0.15.0    	Prometheus exporter for Memcached metrics         
prometheus-community/prometheus-modbus-exporter   	0.1.2        	0.4.1      	A Helm chart for prometheus-modbus-exporter       
prometheus-community/prometheus-mongodb-exporter  	3.9.0        	0.42.0     	A Prometheus exporter for MongoDB metrics         
prometheus-community/prometheus-mysql-exporter    	2.8.0        	v0.16.0    	A Helm chart for prometheus mysql exporter with...
prometheus-community/prometheus-nats-exporter     	2.17.0       	0.15.0     	A Helm chart for prometheus-nats-exporter         
prometheus-community/prometheus-nginx-exporter    	0.2.2        	0.11.0     	A Helm chart for NGINX Prometheus Exporter        
prometheus-community/prometheus-node-exporter     	4.42.0       	1.8.2      	A Helm chart for prometheus node-exporter         
prometheus-community/prometheus-opencost-exporter 	0.1.1        	1.108.0    	Prometheus OpenCost Exporter                      
prometheus-community/prometheus-operator          	9.3.2        	0.38.1     	DEPRECATED - This chart will be renamed. See ht...
prometheus-community/prometheus-operator-admiss...	0.17.0       	0.78.1     	Prometheus Operator Admission Webhook             
prometheus-community/prometheus-operator-crds     	16.0.1       	v0.78.2    	A Helm chart that collects custom resource defi...
prometheus-community/prometheus-pgbouncer-exporter	0.5.0        	v0.10.2    	A Helm chart for prometheus pgbouncer-exporter    
prometheus-community/prometheus-pingdom-exporter  	2.5.0        	20190610-1 	A Helm chart for Prometheus Pingdom Exporter      
prometheus-community/prometheus-pingmesh-exporter 	0.4.0        	v1.2.1     	Prometheus Pingmesh Exporter                      
prometheus-community/prometheus-postgres-exporter 	6.7.1        	v0.16.0    	A Helm chart for prometheus postgres-exporter     
prometheus-community/prometheus-pushgateway       	2.15.0       	v1.10.0    	A Helm chart for prometheus pushgateway           
prometheus-community/prometheus-rabbitmq-exporter 	1.12.1       	v0.29.0    	Rabbitmq metrics exporter for prometheus          
prometheus-community/prometheus-redis-exporter    	6.8.0        	v1.66.0    	Prometheus exporter for Redis metrics             
prometheus-community/prometheus-smartctl-exporter 	0.11.0       	v0.12.0    	A Helm chart for Kubernetes                       
prometheus-community/prometheus-snmp-exporter     	5.6.0        	v0.26.0    	Prometheus SNMP Exporter                          
prometheus-community/prometheus-sql-exporter      	0.2.0        	v0.5.8     	Prometheus SQL Exporter                           
prometheus-community/prometheus-stackdriver-exp...	4.6.2        	v0.16.0    	Stackdriver exporter for Prometheus               
prometheus-community/prometheus-statsd-exporter   	0.15.0       	v0.28.0    	A Helm chart for prometheus stats-exporter        
prometheus-community/prometheus-systemd-exporter  	0.3.0        	0.6.0      	A Helm chart for prometheus systemd-exporter      
prometheus-community/prometheus-to-sd             	0.4.2        	0.5.2      	Scrape metrics stored in prometheus format and ...
prometheus-community/prometheus-windows-exporter  	0.7.1        	0.29.2     	A Helm chart for prometheus windows-exporter      
prometheus-community/alertmanager                 	1.13.1       	v0.27.0    	The Alertmanager handles alerts sent by client ...
prometheus-community/alertmanager-snmp-notifier   	0.4.0        	v1.6.0     	The SNMP Notifier handles alerts coming from Pr...
prometheus-community/jiralert                     	1.7.2        	v1.3.0     	A Helm chart for Kubernetes to install jiralert   
prometheus-community/kube-state-metrics           	5.27.0       	2.14.0     	Install kube-state-metrics to generate and expo...
prometheus-community/prom-label-proxy             	0.10.0       	v0.11.0    	A proxy that enforces a given label in a given ...
bitnami/grafana-mimir                             	1.2.22       	2.14.2     	Grafana Mimir is an open source, horizontally s...
bitnami/node-exporter                             	4.4.17       	1.8.2      	Prometheus exporter for hardware and OS metrics...
bitnami/thanos                                    	15.8.1       	0.36.1     	Thanos is a highly available metrics system tha...
bitnami/kube-state-metrics                        	4.2.16       	2.14.0     	kube-state-metrics is a simple service that lis...
bitnami/mariadb                                   	20.0.0       	11.4.4     	MariaDB is an open source, community-developed ...
bitnami/mariadb-galera                            	14.0.12      	11.4.4     	MariaDB Galera is a multi-primary database clus...
mukeshurmaliya@MASK ~ % helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "prometheus-community" chart repository
...Successfully got an update from the "bitnami" chart repository
Update Complete. ⎈Happy Helming!⎈
mukeshurmaliya@MASK ~ % helm install prometheus prometheus-community/prometheus 
NAME: prometheus
LAST DEPLOYED: Wed Dec 11 10:55:39 2024
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
The Prometheus server can be accessed via port 80 on the following DNS name from within your cluster:
prometheus-server.default.svc.cluster.local


Get the Prometheus server URL by running these commands in the same shell:
  export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=prometheus,app.kubernetes.io/instance=prometheus" -o jsonpath="{.items[0].metadata.name}")
  kubectl --namespace default port-forward $POD_NAME 9090


The Prometheus alertmanager can be accessed via port 9093 on the following DNS name from within your cluster:
prometheus-alertmanager.default.svc.cluster.local


Get the Alertmanager URL by running these commands in the same shell:
  export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=alertmanager,app.kubernetes.io/instance=prometheus" -o jsonpath="{.items[0].metadata.name}")
  kubectl --namespace default port-forward $POD_NAME 9093
#################################################################################
######   WARNING: Pod Security Policy has been disabled by default since    #####
######            it deprecated after k8s 1.25+. use                        #####
######            (index .Values "prometheus-node-exporter" "rbac"          #####
###### .          "pspEnabled") with (index .Values                         #####
######            "prometheus-node-exporter" "rbac" "pspAnnotations")       #####
######            in case you still need it.                                #####
#################################################################################


The Prometheus PushGateway can be accessed via port 9091 on the following DNS name from within your cluster:
prometheus-prometheus-pushgateway.default.svc.cluster.local


Get the PushGateway URL by running these commands in the same shell:
  export POD_NAME=$(kubectl get pods --namespace default -l "app=prometheus-pushgateway,component=pushgateway" -o jsonpath="{.items[0].metadata.name}")
  kubectl --namespace default port-forward $POD_NAME 9091

For more information on running Prometheus, visit:
https://prometheus.io/
mukeshurmaliya@MASK ~ % kubectl get all 
NAME                                                     READY   STATUS    RESTARTS      AGE
pod/mynginxws-84b5485f7c-lvg7n                           1/1     Running   2 (33m ago)   17d
pod/prometheus-alertmanager-0                            1/1     Running   0             18m
pod/prometheus-kube-state-metrics-86969d697f-64b7d       1/1     Running   0             18m
pod/prometheus-prometheus-node-exporter-hbpgs            1/1     Running   0             18m
pod/prometheus-prometheus-pushgateway-85b7d9fbfc-gjnhl   1/1     Running   0             18m
pod/prometheus-server-5ff7d977b4-cw6dv                   2/2     Running   0             18m

NAME                                          TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
service/kubernetes                            ClusterIP      10.96.0.1        <none>        443/TCP                      205d
service/mongo-service                         ClusterIP      10.102.101.102   <none>        8080/TCP                     171d
service/mynginxws                             LoadBalancer   10.103.248.174   <pending>     80:30695/TCP,443:31584/TCP   17d
service/prometheus-alertmanager               ClusterIP      10.105.199.107   <none>        9093/TCP                     18m
service/prometheus-alertmanager-headless      ClusterIP      None             <none>        9093/TCP                     18m
service/prometheus-kube-state-metrics         ClusterIP      10.100.1.62      <none>        8080/TCP                     18m
service/prometheus-prometheus-node-exporter   ClusterIP      10.104.3.187     <none>        9100/TCP                     18m
service/prometheus-prometheus-pushgateway     ClusterIP      10.110.121.95    <none>        9091/TCP                     18m
service/prometheus-server                     ClusterIP      10.100.49.12     <none>        80/TCP                       18m

NAME                                                 DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR            AGE
daemonset.apps/prometheus-prometheus-node-exporter   1         1         1       1            1           kubernetes.io/os=linux   18m

NAME                                                READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/mynginxws                           1/1     1            1           17d
deployment.apps/prometheus-kube-state-metrics       1/1     1            1           18m
deployment.apps/prometheus-prometheus-pushgateway   1/1     1            1           18m
deployment.apps/prometheus-server                   1/1     1            1           18m

NAME                                                           DESIRED   CURRENT   READY   AGE
replicaset.apps/mynginxws-84b5485f7c                           1         1         1       17d
replicaset.apps/prometheus-kube-state-metrics-86969d697f       1         1         1       18m
replicaset.apps/prometheus-prometheus-pushgateway-85b7d9fbfc   1         1         1       18m
replicaset.apps/prometheus-server-5ff7d977b4                   1         1         1       18m

NAME                                       READY   AGE
statefulset.apps/prometheus-alertmanager   1/1     18m
mukeshurmaliya@MASK ~ % kubectl get services   
NAME                                  TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
kubernetes                            ClusterIP      10.96.0.1        <none>        443/TCP                      205d
mongo-service                         ClusterIP      10.102.101.102   <none>        8080/TCP                     171d
mynginxws                             LoadBalancer   10.103.248.174   <pending>     80:30695/TCP,443:31584/TCP   17d
prometheus-alertmanager               ClusterIP      10.105.199.107   <none>        9093/TCP                     21m
prometheus-alertmanager-headless      ClusterIP      None             <none>        9093/TCP                     21m
prometheus-kube-state-metrics         ClusterIP      10.100.1.62      <none>        8080/TCP                     21m
prometheus-prometheus-node-exporter   ClusterIP      10.104.3.187     <none>        9100/TCP                     21m
prometheus-prometheus-pushgateway     ClusterIP      10.110.121.95    <none>        9091/TCP                     21m
prometheus-server                     ClusterIP      10.100.49.12     <none>        80/TCP                       21m
mukeshurmaliya@MASK ~ % kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=prometheus-server-ext
service/prometheus-server-ext exposed
mukeshurmaliya@MASK ~ % kubeectl get svc
zsh: command not found: kubeectl
mukeshurmaliya@MASK ~ % kubectl get svc 
NAME                                  TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
kubernetes                            ClusterIP      10.96.0.1        <none>        443/TCP                      205d
mongo-service                         ClusterIP      10.102.101.102   <none>        8080/TCP                     171d
mynginxws                             LoadBalancer   10.103.248.174   <pending>     80:30695/TCP,443:31584/TCP   17d
prometheus-alertmanager               ClusterIP      10.105.199.107   <none>        9093/TCP                     34m
prometheus-alertmanager-headless      ClusterIP      None             <none>        9093/TCP                     34m
prometheus-kube-state-metrics         ClusterIP      10.100.1.62      <none>        8080/TCP                     34m
prometheus-prometheus-node-exporter   ClusterIP      10.104.3.187     <none>        9100/TCP                     34m
prometheus-prometheus-pushgateway     ClusterIP      10.110.121.95    <none>        9091/TCP                     34m
prometheus-server                     ClusterIP      10.100.49.12     <none>        80/TCP                       34m
prometheus-server-ext                 NodePort       10.109.249.59    <none>        80:30258/TCP                 34s
mukeshurmaliya@MASK ~ % minikube service prometheus-server-ext
|-----------|-----------------------|-------------|--------------------------|
| NAMESPACE |         NAME          | TARGET PORT |           URL            |
|-----------|-----------------------|-------------|--------------------------|
| default   | prometheus-server-ext |          80 | http://192.168.6.4:30258 |
|-----------|-----------------------|-------------|--------------------------|
🎉  Opening service default/prometheus-server-ext in default browser...
mukeshurmaliya@MASK ~ % helm repo add grafana https://grafana.github.io/helm-charts
"grafana" has been added to your repositories
mukeshurmaliya@MASK ~ % helm install grafana stable/grafana                        
Error: INSTALLATION FAILED: repo stable not found
mukeshurmaliya@MASK ~ % helm repo update                                                                                        
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "grafana" chart repository
...Successfully got an update from the "prometheus-community" chart repository
...Successfully got an update from the "bitnami" chart repository
Update Complete. ⎈Happy Helming!⎈
mukeshurmaliya@MASK ~ % helm search repo grafana                                                                                
NAME                                          	CHART VERSION	APP VERSION	DESCRIPTION                                       
bitnami/grafana                               	11.4.0       	11.3.0     	Grafana is an open source metric analytics and ...
bitnami/grafana-loki                          	4.7.0        	3.3.1      	Grafana Loki is a horizontally scalable, highly...
bitnami/grafana-mimir                         	1.3.0        	2.14.2     	Grafana Mimir is an open source, horizontally s...
bitnami/grafana-operator                      	4.9.0        	5.15.1     	Grafana Operator is a Kubernetes operator that ...
bitnami/grafana-tempo                         	3.8.0        	2.6.1      	Grafana Tempo is a distributed tracing system t...
grafana/grafana                               	8.6.4        	11.3.1     	The leading tool for querying and visualizing t...
grafana/grafana-agent                         	0.42.0       	v0.42.0    	Grafana Agent                                     
grafana/grafana-agent-operator                	0.5.0        	0.43.3     	A Helm chart for Grafana Agent Operator           
grafana/grafana-operator                      	v5.15.1      	v5.15.1    	Helm chart for the Grafana Operator               
grafana/grafana-sampling                      	1.1.0        	v1.3.0     	A Helm chart for a layered OTLP tail sampling a...
grafana/alloy                                 	0.10.1       	v1.5.1     	Grafana Alloy                                     
grafana/beyla                                 	1.5.0        	1.9.0      	eBPF-based autoinstrumentation HTTP, HTTP2 and ...
grafana/enterprise-logs                       	2.5.0        	v1.5.2     	Grafana Enterprise Logs                           
grafana/enterprise-logs-simple                	1.3.0        	v1.4.0     	DEPRECATED Grafana Enterprise Logs (Simple Scal...
grafana/enterprise-metrics                    	1.10.0       	v1.7.0     	DEPRECATED Grafana Enterprise Metrics             
grafana/fluent-bit                            	2.6.0        	v2.1.0     	Uses fluent-bit Loki go plugin for gathering lo...
grafana/k6-operator                           	3.10.1       	0.0.18     	A Helm chart to install the k6-operator           
grafana/k8s-monitoring                        	1.6.14       	2.10.0     	A Helm chart for gathering, scraping, and forwa...
grafana/lgtm-distributed                      	2.1.0        	^7.3.9     	Umbrella chart for a distributed Loki, Grafana,...
grafana/loki                                  	6.23.0       	3.3.1      	Helm chart for Grafana Loki and Grafana Enterpr...
grafana/loki-canary                           	0.14.0       	2.9.1      	Helm chart for Grafana Loki Canary                
grafana/loki-distributed                      	0.80.0       	2.9.10     	Helm chart for Grafana Loki in microservices mode 
grafana/loki-simple-scalable                  	1.8.11       	2.6.1      	Helm chart for Grafana Loki in simple, scalable...
grafana/loki-stack                            	2.10.2       	v2.9.3     	Loki: like Prometheus, but for logs.              
grafana/meta-monitoring                       	1.3.0        	0.0.1      	A Helm chart for meta monitoring Grafana Loki, ...
grafana/mimir-distributed                     	5.5.1        	2.14.0     	Grafana Mimir                                     
grafana/mimir-openshift-experimental          	2.1.0        	2.0.0      	Grafana Mimir on OpenShift Experiment             
grafana/oncall                                	1.13.9       	v1.13.9    	Developer-friendly incident response with brill...
grafana/phlare                                	0.5.4        	0.5.1      	🔥 horizontally-scalable, highly-available, mul...
grafana/promtail                              	6.16.6       	3.0.0      	Promtail is an agent which ships the contents o...
grafana/pyroscope                             	1.10.0       	1.10.0     	🔥 horizontally-scalable, highly-available, mul...
grafana/rollout-operator                      	0.21.0       	v0.21.0    	Grafana rollout-operator                          
grafana/snyk-exporter                         	0.1.0        	v1.4.1     	Prometheus exporter for Snyk.                     
grafana/synthetic-monitoring-agent            	0.6.0        	v0.29.3    	Grafana's Synthetic Monitoring application. The...
grafana/tempo                                 	1.15.0       	2.6.1      	Grafana Tempo Single Binary Mode                  
grafana/tempo-distributed                     	1.25.1       	2.6.0      	Grafana Tempo in MicroService mode                
grafana/tempo-vulture                         	0.7.1        	2.6.1      	Grafana Tempo Vulture - A tool to monitor Tempo...
prometheus-community/kube-prometheus-stack    	66.3.1       	v0.78.2    	kube-prometheus-stack collects Kubernetes manif...
prometheus-community/prometheus-druid-exporter	1.1.0        	v0.11.0    	Druid exporter to monitor druid metrics with Pr...
mukeshurmaliya@MASK ~ % helm install grafana grafana/grafana
NAME: grafana
LAST DEPLOYED: Wed Dec 11 11:58:08 2024
NAMESPACE: default
STATUS: deployed
REVISION: 1
NOTES:
1. Get your 'admin' user password by running:

   kubectl get secret --namespace default grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo


2. The Grafana server can be accessed via port 80 on the following DNS name from within your cluster:

   grafana.default.svc.cluster.local

   Get the Grafana URL to visit by running these commands in the same shell:
     export POD_NAME=$(kubectl get pods --namespace default -l "app.kubernetes.io/name=grafana,app.kubernetes.io/instance=grafana" -o jsonpath="{.items[0].metadata.name}")
     kubectl --namespace default port-forward $POD_NAME 3000

3. Login with the password from step 1 and the username: admin
#################################################################################
######   WARNING: Persistence is disabled!!! You will lose your data when   #####
######            the Grafana pod is terminated.                            #####
#################################################################################
mukeshurmaliya@MASK ~ % heelm list
zsh: command not found: heelm
mukeshurmaliya@MASK ~ % helm list 
NAME      	NAMESPACE	REVISION	UPDATED                             	STATUS  	CHART            	APP VERSION
grafana   	default  	1       	2024-12-11 11:58:08.446066 +0100 CET	deployed	grafana-8.6.4    	11.3.1     
mynginxws 	default  	1       	2024-11-24 09:37:23.719647 +0100 CET	deployed	nginx-18.2.5     	1.27.2     
prometheus	default  	1       	2024-12-11 10:55:39.072535 +0100 CET	deployed	prometheus-26.0.0	v3.0.0     
mukeshurmaliya@MASK ~ % kubectl get secret --namespace default grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
v05VgYbUbUwQEsG5HN0DHFFiUIqxTkibzt3fWj2h
mukeshurmaliya@MASK ~ % kubectl get all
NAME                                                     READY   STATUS    RESTARTS      AGE
pod/grafana-659975ff68-rzff4                             1/1     Running   0             75s
pod/mynginxws-84b5485f7c-lvg7n                           1/1     Running   2 (79m ago)   17d
pod/prometheus-alertmanager-0                            1/1     Running   0             64m
pod/prometheus-kube-state-metrics-86969d697f-64b7d       1/1     Running   0             64m
pod/prometheus-prometheus-node-exporter-hbpgs            1/1     Running   0             64m
pod/prometheus-prometheus-pushgateway-85b7d9fbfc-gjnhl   1/1     Running   0             64m
pod/prometheus-server-5ff7d977b4-cw6dv                   2/2     Running   0             64m

NAME                                          TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
service/grafana                               ClusterIP      10.105.140.32    <none>        80/TCP                       76s
service/kubernetes                            ClusterIP      10.96.0.1        <none>        443/TCP                      205d
service/mongo-service                         ClusterIP      10.102.101.102   <none>        8080/TCP                     171d
service/mynginxws                             LoadBalancer   10.103.248.174   <pending>     80:30695/TCP,443:31584/TCP   17d
service/prometheus-alertmanager               ClusterIP      10.105.199.107   <none>        9093/TCP                     64m
service/prometheus-alertmanager-headless      ClusterIP      None             <none>        9093/TCP                     64m
service/prometheus-kube-state-metrics         ClusterIP      10.100.1.62      <none>        8080/TCP                     64m
service/prometheus-prometheus-node-exporter   ClusterIP      10.104.3.187     <none>        9100/TCP                     64m
service/prometheus-prometheus-pushgateway     ClusterIP      10.110.121.95    <none>        9091/TCP                     64m
service/prometheus-server                     ClusterIP      10.100.49.12     <none>        80/TCP                       64m
service/prometheus-server-ext                 NodePort       10.109.249.59    <none>        80:30258/TCP                 30m

NAME                                                 DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR            AGE
daemonset.apps/prometheus-prometheus-node-exporter   1         1         1       1            1           kubernetes.io/os=linux   64m

NAME                                                READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/grafana                             1/1     1            1           75s
deployment.apps/mynginxws                           1/1     1            1           17d
deployment.apps/prometheus-kube-state-metrics       1/1     1            1           64m
deployment.apps/prometheus-prometheus-pushgateway   1/1     1            1           64m
deployment.apps/prometheus-server                   1/1     1            1           64m

NAME                                                           DESIRED   CURRENT   READY   AGE
replicaset.apps/grafana-659975ff68                             1         1         1       75s
replicaset.apps/mynginxws-84b5485f7c                           1         1         1       17d
replicaset.apps/prometheus-kube-state-metrics-86969d697f       1         1         1       64m
replicaset.apps/prometheus-prometheus-pushgateway-85b7d9fbfc   1         1         1       64m
replicaset.apps/prometheus-server-5ff7d977b4                   1         1         1       64m

NAME                                       READY   AGE
statefulset.apps/prometheus-alertmanager   1/1     64m
mukeshurmaliya@MASK ~ % kubectl expose service grafana --type=NodePort --target-port=3000 --name=grafana-ext
service/grafana-ext exposed
mukeshurmaliya@MASK ~ % kubectl get svc                                                                                             
NAME                                  TYPE           CLUSTER-IP       EXTERNAL-IP   PORT(S)                      AGE
grafana                               ClusterIP      10.105.140.32    <none>        80/TCP                       3m10s
grafana-ext                           NodePort       10.102.63.79     <none>        80:32207/TCP                 7s
kubernetes                            ClusterIP      10.96.0.1        <none>        443/TCP                      205d
mongo-service                         ClusterIP      10.102.101.102   <none>        8080/TCP                     171d
mynginxws                             LoadBalancer   10.103.248.174   <pending>     80:30695/TCP,443:31584/TCP   17d
prometheus-alertmanager               ClusterIP      10.105.199.107   <none>        9093/TCP                     65m
prometheus-alertmanager-headless      ClusterIP      None             <none>        9093/TCP                     65m
prometheus-kube-state-metrics         ClusterIP      10.100.1.62      <none>        8080/TCP                     65m
prometheus-prometheus-node-exporter   ClusterIP      10.104.3.187     <none>        9100/TCP                     65m
prometheus-prometheus-pushgateway     ClusterIP      10.110.121.95    <none>        9091/TCP                     65m
prometheus-server                     ClusterIP      10.100.49.12     <none>        80/TCP                       65m
prometheus-server-ext                 NodePort       10.109.249.59    <none>        80:30258/TCP                 32m
mukeshurmaliya@MASK ~ % minikube service grafana-ext
|-----------|-------------|-------------|--------------------------|
| NAMESPACE |    NAME     | TARGET PORT |           URL            |
|-----------|-------------|-------------|--------------------------|
| default   | grafana-ext |          80 | http://192.168.6.4:32207 |
|-----------|-------------|-------------|--------------------------|
🎉  Opening service default/grafana-ext in default browser...
mukeshurmaliya@MASK ~ % 
