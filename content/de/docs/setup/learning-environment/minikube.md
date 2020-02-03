---
reviewers:
title: Kubernetes mit Minikube installieren
content_template: templates/concept
---

{{% capture overview %}}

Minikube ist ein Tool um den Betrieb von Kubernetes auf einer lokalen Umgebung zu erleichtern. Minikube startet einen Kubernetes-Cluster mit einem Node in einer virtuellen Maschine (VM) auf Ihrem Laptop, um Kubernetes auszuprobieren oder um darauf täglich zu entwickeln.

{{% /capture %}}

{{% capture body %}}

## Minikube Features

Minikube unterstützt die folgenden Funktionen

* DNS
* NodePorts
* ConfigMaps und Secrets
* Dashboards
* Container Runtime: Docker, [CRI-O](https://cri-o.io/), and [containerd](https://github.com/containerd/containerd)
* CNI aktivieren (Container Network Interface)
* Ingress

## Installation

Siehe [Installation von Minikube](/de/docs/tasks/tools/install-minikube/).

## Schnellstart

Diese Kurzanleitung begleitet Sie bei Ihrem ersten Start, der Benutzung und beim Löschen eines lokalen Minikube-Clusters. Folgen Sie den Schritten unten und probieren Sie Minikube aus.

1. Minikube starten und einen Cluster anlegen:
    ```shell
    minikube start
    ```
    Die Ausgabe sollte so ähnlich aussehen:

    ```
    Starting local Kubernetes cluster...
    Running pre-create checks...
    Creating machine...
    Starting local Kubernetes cluster...
    ```
    Für mehr Informationen zum Start eines Clusters einer spezifischen Kubernetes-Version, VM oder eine Container-Laufzeitumgebung, siehe [Start eines Clusters](#starten-eines-clusters).

2. Jetzt können Sie mit dem Cluster per `kubectl` interagieren. Für mehr Informationen, siehe [Mit dem Cluster interagieren](#mit-dem-cluster-interagieren).

    Im nächsten Schritt wird ein Kubernetes-Deployment mit einem existierenden Image namens `echoserver` erstellt, der einen einfachen HTTP Server bereitstellt und per `--port` auf Port 8080 verfügbar macht.
    ```shell
    kubectl create deployment hello-minikube --image=k8s.gcr.io/echoserver:1.10
    ```
    Die Ausgabe sollte so ähnlich aussehen:
    ```
    deployment.apps/hello-minikube created
    ```
3. Machen Sie das Deployment als Service verfügbar, um Zugang zum Deployment `hello-minikube` zu bekommen:
    ```shell
    kubectl expose deployment hello-minikube --type=NodePort --port=8080
    ```
    Die Option `--type=NodePort` gibt den Typ des Services an.

    Die Ausgabe sollte so ähnlich aussehen:
    ```
    service/hello-minikube exposed
    ```
4. Der Pod `hello-minikube` ist jetzt gestartet, aber Sie müssen warten, bis der Pod vollständig hochgefahren ist, bevor der Zugang über den verfügbar gemachten Service bereit ist.

	Prüfen Sie, ob der Pod bereit ist:
	```shell
	kubectl get pod
	```
	Wenn die Ausgabe den `STATUS` als `ContainerCreating` anzeigt, wird der Pod noch gestartet:
	```
	NAME                              READY     STATUS              RESTARTS   AGE
	hello-minikube-3383150820-vctvh   0/1       ContainerCreating   0          3s
	```
	Wenn die Ausgabe den `STATUS` als `Running` anzeigt, ist der Pod vollständig hochgefahren und bereit:
	```
	NAME                              READY     STATUS    RESTARTS   AGE
	hello-minikube-3383150820-vctvh   1/1       Running   0          13s
	```
5. Fragen Sie die URL des verfügbar gemachten Service ab, um Details anzuzeigen:
	```shell
	minikube service hello-minikube --url
	```
6. Um die Details des lokalen Clusters anzuzeigen, kopieren Sie die URL und öffnen Sie sie mit Ihrem Browser.

    Die Ausgabe sollte so ähnlich aussehen:
    ```
    Hostname: hello-minikube-7c77b68cff-8wdzq

    Pod Information:
        -no pod information available-

    Server values:
        server_version=nginx: 1.13.3 - lua: 10008

    Request Information:
        client_address=172.17.0.1
        method=GET
        real path=/
        query=
        request_version=1.1
        request_scheme=http
        request_uri=http://192.168.99.100:8080/

    Request Headers:
        accept=*/*
        host=192.168.99.100:30674
        user-agent=curl/7.47.0

    Request Body:
        -no body in request-
    ```
	Wenn Sie den Service und den Cluster nicht länger brauchen, können Sie sie löschen.
7. Löschen Sie den Service `hello-minikube`:
    ```shell
    kubectl delete services hello-minikube
    ```
    Die Ausgabe sollte so ähnlich aussehen:
    ```
    service "hello-minikube" deleted
    ```
8. Löschen Sie das Deployment `hello-minikube`:
    ```shell
    kubectl delete deployment hello-minikube
    ```
    Die Ausgabe sollte so ähnlich aussehen:
    ```
    deployment.extensions "hello-minikube" deleted
    ```
9. Stoppen Sie den lokalen Minikube-Cluster:
    ```shell
    minikube stop
    ```
    Die Ausgabe sollte so ähnlich aussehen:
    ```
    Stopping "minikube"...
    "minikube" stopped.
    ```
	Für mehr Informationen, siehe [Stoppen eines Clusters](#stoppen-eines-clusters).
10. Löschen Sie den lokalen Minikube-Cluster:
    ```shell
    minikube delete
    ```
    Die Ausgabe sollte so ähnlich aussehen:
    ```
    Deleting "minikube" ...
    The "minikube" cluster has been deleted.
    ```
	Für mehr Informationen, siehe [Löschen eines Clusters](#löschen-eines-clusters).

## Verwalten des Clusters

### Starten eines Clusters

Das Kommando `minikube start` wird zum Start eines Clusters verwendet. Dieses Kommando erstellt und konfiguriert eines virtuelle Maschine mit einem Kubernetes-Cluster mit einem einzelnen Node. Das Kommando konfiguriert ausserdem [kubectl](/docs/user-guide/kubectl-overview/) zur Kommunikation mit dem Cluster.

{{< note >}}
Sollten Sie hinter einem Web-Proxy sein, müssen sie die Proxy-Informationen an das Kommando `minikube start` übergeben:

```shell
https_proxy=<mein proxy> minikube start --docker-env http_proxy=<mein proxy> --docker-env https_proxy=<mein proxy> --docker-env no_proxy=192.168.99.0/24
```
Leider reicht das Setzen der Umgebungsvariablen allein nicht aus.

Minikube erstellt auch einen "minikube" Kontext und setzt diesen als Standard in kubectl. Um zu diesem Kontakt zu wechseln, führen Sie dieses Kommando aus: `kubectl config use-context minikube`.
{{< /note >}}

#### Angeben der Version für Kubernetes

Sie können die Version von Kubernetes angeben, die von Minikube verwendet wird. Dazu fügen Sie die Option `--kubernetes-version` zum Kommando `minikube start` hinzu. Um zum Beispiel die Version {{< param "fullversion" >}} zu verwenden, führen Sie das folgende Kommando aus:

```
minikube start --kubernetes-version {{< param "fullversion" >}}
```
#### Angeben der Treiber für die VM
Sie können die Treiber für die VM ändern, in dem Sie die Option `--vm-driver=<treiber_name_angeben>` zum Kommando `minikube start` hinzufügen.
Das Kommando wäre wie folgt:
```shell
minikube start --vm-driver=<driver_name>
```
Minikube unterstützt die folgenden Treiber:
{{< note >}}
Siehe [Drivers](https://minikube.sigs.k8s.io/docs/reference/drivers/) für Einzelheiten zu unterstützten Treibern und der Installationsanleitung für Plugins.
{{< /note >}}

* hyperkit ([driver installation](https://minikube.sigs.k8s.io/docs/reference/drivers/hyperkit/))
* hyperv ([driver installation](https://minikube.sigs.k8s.io/docs/reference/drivers/hyperv/))
* kvm2 ([driver installation](https://minikube.sigs.k8s.io/docs/reference/drivers/kvm2/))
* parallels
* virtualbox ([driver installation](https://minikube.sigs.k8s.io/docs/reference/drivers/virtualbox/))
* vmware ([driver installation](https://minikube.sigs.k8s.io/docs/reference/drivers/vmware/))
* none (Startet die Komponenten von Kubernetes auf dem Host und nicht in einer VM. Es wird nicht empfohlen, den Treiber "none" auf einer lokalen Umgebung zu betreiben.)

#### Start eines Clusters auf einer alternativen Container-Laufzeitumgebung
Sie können Minikube auf den folgenden Container-Laufzeitumgebungen starten:
{{< tabs name="container_runtimes" >}}
{{% tab name="containerd" %}}
Um [containerd](https://github.com/containerd/containerd) als Laufzeitumgebung zu verwenden, führen Sie das folgende Kommando aus:
```bash
minikube start \
    --network-plugin=cni \
    --enable-default-cni \
    --container-runtime=containerd \
    --bootstrapper=kubeadm
```
Sie können auch die erweiterte Version verwenden:

```bash
minikube start \
    --network-plugin=cni \
    --enable-default-cni \
    --extra-config=kubelet.container-runtime=remote \
    --extra-config=kubelet.container-runtime-endpoint=unix:///run/containerd/containerd.sock \
    --extra-config=kubelet.image-service-endpoint=unix:///run/containerd/containerd.sock \
    --bootstrapper=kubeadm
```
{{% /tab %}}
{{% tab name="CRI-O" %}}
Um [CRI-O](https://cri-o.io/) als Laufzeitumgebung zu verwenden, führen Sie das folgende Kommando aus:
```bash
minikube start \
    --network-plugin=cni \
    --enable-default-cni \
    --container-runtime=cri-o \
    --bootstrapper=kubeadm
```
Sie können auch die erweiterte Version verwenden:

```bash
minikube start \
    --network-plugin=cni \
    --enable-default-cni \
    --extra-config=kubelet.container-runtime=remote \
    --extra-config=kubelet.container-runtime-endpoint=/var/run/crio.sock \
    --extra-config=kubelet.image-service-endpoint=/var/run/crio.sock \
    --bootstrapper=kubeadm
```
{{% /tab %}}
{{< /tabs >}}

#### Lokale Images durch die Wiederverwendung des Docker Daemon benutzen

Wenn Sie eine einzelne VM für Kubernetes benutzen, ist es nützlich, den eingebauten Docker Daemon von Minikube zu verwenden. Die Wiederverwendung des eingebauten Daemon zu verwenden hat den Vorteil, das keine zusätzliche Docker Registry auf Ihrer Maschine betrieben und das Image dorthin gepusht werden muss. Stattdessen können Sie in den selben Daemon wie Minikube verwenden, so dass lokale Experimente beschleunigt werden.

{{< note >}}
Stellen Sie sicher, dass Ihre Docker Image einen anderen Tag als "latest" verwenden und das dieser Tag verwendet wird, um das Image zu pullen. Da `:latest` der Standardwert ist, kann ein Fehler beim Abrufen des Images (`ErrImagePull`) auftreten, sollte das Docker Image nicht in der Standard Docker Registry (für gewöhnlich DockerHub) verfügbar sein.
{{< /note >}}

Um mit dem Docker Daemon auf Ihrem Mac/Linux Host zu arbeiten, verwenden Sie das `docker-env command` in ihrem Terminal:

```shell
eval $(minikube docker-env)
```

Sie können jetzt Docker auf der Kommandozeile benutzen, um mit dem Docker Daemon innerhalb der Minikube VM zu kommunizieren:

```shell
docker ps
```

{{< note >}}
Auf Centos 7 könnte Docker den folgenden Fehler anzeigen:

```
Could not read CA certificate "/etc/docker/ca.pem": open /etc/docker/ca.pem: no such file or directory
```
Dieser Fehler kann behoben werden, in dem die Datei /etc/sysconfig/docker so angepasst wird, dass die Umgebung von Minikube respektiert wird:

```shell
< DOCKER_CERT_PATH=/etc/docker
---
> if [ -z "${DOCKER_CERT_PATH}" ]; then
>   DOCKER_CERT_PATH=/etc/docker
> fi
```
{{< /note >}}

### Kubernetes konfigurieren

Minikube hat eine Konfigurationsfunktion, die es Benutzern erlaubt, die Komponenten von Kubernetes mit beliebigen Werten zu konfigurieren. Um dieses Feature zu verwenden, können Sie die Option `--extra-config` zu dem Kommando `minikube start` hinzufügen.

Diese Option kann wiederholt werden, so dass mehrere Konfigurationen mit unterschiedlichen Werten gleichzeitig gesetzt werden können.

Die Option nimmt eine Zeichenkette in der Form `component.key=value` entgegen, wobei `component` eine der Zeichenkette aus der Liste unten, `key` die Bezeichnung der Konfiguration und `value` der zu setzende Wert der Konfiguration ist.

Gültige Bezeichnungen können der Dokumentation der Kubernetes `componentconfigs` jeder Komponente entnommen werden.
Hier ist die Dokumentation für alle unterstützten Konfigurationen:

* [kubelet](https://godoc.org/k8s.io/kubernetes/pkg/kubelet/apis/config#KubeletConfiguration)
* [apiserver](https://godoc.org/k8s.io/kubernetes/cmd/kube-apiserver/app/options#ServerRunOptions)
* [proxy](https://godoc.org/k8s.io/kubernetes/pkg/proxy/apis/config#KubeProxyConfiguration)
* [controller-manager](https://godoc.org/k8s.io/kubernetes/pkg/controller/apis/config#KubeControllerManagerConfiguration)
* [etcd](https://godoc.org/github.com/coreos/etcd/etcdserver#ServerConfig)
* [scheduler](https://godoc.org/k8s.io/kubernetes/pkg/scheduler/apis/config#KubeSchedulerConfiguration)

#### Beispiele

Um die Konfiguration `MaxPods` des Kubelet auf 5 zu setzen, geben Sie die folgende Option an: `--extra-config=kubelet.MaxPods=5`.

Diese Funktion unterstützt auch verschachtelte Strukturen. Um die Konfiguration `LeaderElection.LeaderElect` des Scheduler auf `true` zu setzen, geben Sie die folgende Option an: `--extra-config=scheduler.LeaderElection.LeaderElect=true`.

Um den `AuthorizationMode` des API-Server auf `RBAC` zu setzen, geben Sie die folgende Option an: `--extra-config=apiserver.authorization-mode=RBAC`.

### Stoppen des Clusters
Das Kommando `minikube stop` wird verwendet, um den Cluster zu stoppen.
Dieses Kommando stoppt die VM von Minikube, löscht aber den Zustand und die Daten des Clusters nicht.
Der erneute Start des Clusters stellt den vorherigen Zustand wieder her.

### Löschen des Clusters
Das Kommando `minikube delete` wird verwendet, um den Cluster zu löschen.
Dieses Kommando stoppt und löscht die VM von Minikube. Der Zustand und die Daten des Clusters werden entfernt.

### Upgrading minikube
Siehe [upgrade minikube](https://minikube.sigs.k8s.io/docs/start/macos/)

## Mit dem Cluster interagieren

### Kubectl

Das Kommando `minikube start` erstellt einen [kubectl Kontext](/docs/reference/generated/kubectl/kubectl-commands#-em-set-context-em-) namens "minikube".
Dieser Kontext enthält die Konfiguration, um mit dem Minikube-Cluster zu kommunizieren.

Minikube setzt diesen Kontakt automatisch als Standard, aber wenn Sie später zu diesem Kontext zurückwechseln wollen, geben Sie folgendes Kommando ein:

`kubectl config use-context minikube`,

Oder geben Sie den Kontext bei jedem Kommando wie folgt an: `kubectl get pods --context=minikube`.

### Dashboard

Um auf das [Kubernetes Dashboard](/docs/tasks/access-application-cluster/web-ui-dashboard/) zuzugreifen, geben Sie das folgende Kommando nach dem Start der Minikube ein:

```shell
minikube dashboard
```

### Services

Um auf einen Service per NodePort zuzugreifen, geben Sie das folgende Kommando nach dem Start der Minikube ein:

```shell
minikube service [-n NAMESPACE] [--url] SERVICE_NAME
```

## Netzwerk

Die VM der Minikube ist auf dem Host via host-only IP-Adresse zugänglich. Die Adresse kann mit dem Kommando `minikube ip` angezeigt werden.
Alle Services vom Typ `NodePort` können über diese IP-Adresse mit dem NodePort aufgerufen werden.

Um den NodePort für einen Service anzuzeigen, verwenden Sie das folgende `kubectl` Kommando:

`kubectl get service $SERVICE --output='jsonpath="{.spec.ports[0].nodePort}"'`

## Persistente Speicher
Minikube unterstützt [PersistentVolume](/docs/concepts/storage/persistent-volumes/) vom Typ `hostPath`.
Diese PersistentVolume werden in ein Verzeichnis innerhalb der VM der Minikube verknüpft.

Die VM der Minikube startet in ein tmpffs, so dass die meisten Verzeichnisse nicht über einen Neustart (`minikube stop`) persistiert werden. Allerdings ist Minikube so konfiguriert, dass die Dateien in den folgenden Verzeichnissen auf dem Host abgelegt werden:

* `/data`
* `/var/lib/minikube`
* `/var/lib/docker`

Hier ist ein Beispiel einer Konfiguration für ein PersistentVolume, um die Daten im Verzeichnis `/data` zu persistieren:

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv0001
spec:
  accessModes:
    - ReadWriteOnce
  capacity:
    storage: 5Gi
  hostPath:
    path: /data/pv0001/
```

## Verknüpfte Verzeichnisse auf dem Host
Einige Treiber verknüpfen ein Verzeichnis auf dem Host mit der VM, so dass auf einfachem Weg Dateien zwischen der VM und dem Host ausgetauscht werden können.  Diese Verzeichnisse sind im Moment nicht konfigurierbar und unterscheiden sich je nach Treiber und genutztem Betriebssystem.

{{< note >}}
Teilen eines Verzeichnisses auf dem Host ist aktuell im Treiber kvm nicht implementiert.
{{< /note >}}

| Treiber | OS | Verzeichnis auf dem Host | VM |
| --- | --- | --- | --- |
| VirtualBox | Linux | /home | /hosthome |
| VirtualBox | macOS | /Users | /Users |
| VirtualBox | Windows | C://Users | /c/Users |
| VMware Fusion | macOS | /Users | /Users |
| Xhyve | macOS | /Users | /Users |

## Private Container Registries

Um auf eine private Container Registry zuzugreifen, folgen Sie den Schritten auf [dieser Seite](/docs/concepts/containers/images/).

Wir schlagen vor, `ImagePullSecrets` zu verwenden, aber falls die Konfiguration innerhalb der VM der Minikube abgelegt werden soll, kann die `.dockercfg` im Verzeichnis `/home/docker` oder die `config.json` im Verzeichnis `/home/docker/.docker` abgelegt werden.

## Add-ons

Damit Minikube benutzerdefinierte Add-Ons erfolgreich starten oder neustarten kann, müssen die Add-Ons im Verzeichnis `~/.minikube/addons` abgelegt werden. Add-Ons in diesem Verzeichnis werden in die VM der Minikube verschoben und bei jedem Start oder Neustart der Minikube ausgeführt.

## Minikube hinter einem HTTP Proxy verwenden

Minikube erstellt eine virtuelle Maschine, die Kubernetes und einen Docker Daemon enthält.
Wenn Kubernetes versucht, einen Container mittels Docker einzuplanen, kann der Docker Daemon auf externe Netzwerke zugreifen, um Container Image herunterzuladen.

Sollten Sie hinter einem HTTP-Proxy sein, muss u.U. der Proxy an den Docker Daemon weitergegeben werden. Um das zu tun, konfigurieren Sie die Umgebungsvariablen als Optionen für das Kommando `minikube start`:

For example:

```shell
minikube start --docker-env http_proxy=http://$YOURPROXY:PORT \
                 --docker-env https_proxy=https://$YOURPROXY:PORT
```

Sollte die Adresse Ihrer virtuellen Maschine 192.168.99.100 sein, könnte es sein, dass Ihre Proxy-Einstellungen den Zugriff von `kubectl` auf die VM verhindern. Um die Proxy-Einstellungen für diese IP-Adresse zu umgehen, sollten Sie Ihre Einstellungen wie folgt verändern:

```shell
export no_proxy=$no_proxy,$(minikube ip)
```

## Bekannte Fehler

Funktionen, die mehrere Node erfordern, werden in Minikube nicht funktionieren.

## Design

Minikube verwendet [libmachine](https://github.com/docker/machine/tree/master/libmachine) für die Bereitstellung von VMs, und [kubeadm](https://github.com/kubernetes/kubeadm) für die Bereitstellung von Kubernetes-Clustern.

Für weitere Informationen über Minikube, siehe [Design Proposal](https://git.k8s.io/community/contributors/design-proposals/cluster-lifecycle/local-cluster-ux.md).

## Weiterführende Links

* **Goals and Non-Goals**: Für die Ziele und Nicht-Ziele des Projektes Minikube, siehe die [Roadmap](https://git.k8s.io/minikube/docs/contributors/roadmap.md).
* **Development Guide**: Siehe [CONTRIBUTING.md](https://git.k8s.io/minikube/CONTRIBUTING.md) für eine Übersicht zur Erstellung von Pull Requests.
* **Building Minikube**: Für Anleitungen zum Bau bzw. Test von Minikube aus den Quellen, siehe [build guide](https://git.k8s.io/minikube/docs/contributors/build_guide.md).
* **Adding a New Dependency**: Für Anleitungen zum Hinzufügen einer neuen Abhängigkeit zu Minikube, siehe [adding dependencies guide](https://git.k8s.io/minikube/docs/contributors/adding_a_dependency.md).
* **Adding a New Addon**: Für Anleitungen zum Hinzufügen eines neuen Add-Ons für Minikube, siehe [adding an addon guide](https://git.k8s.io/minikube/docs/contributors/adding_an_addon.md).
* **MicroK8s**: Linux-Nutzer, die eine zusätzliche virtuelle Maschine vermeiden möchten, sollten [MicroK8s](https://microk8s.io/) als Alternative evaluieren.

## Community

Mitarbeit, Fragen, und Kommentare sind willkommen! Entwickler von Minikube sind im [Slack](https://kubernetes.slack.com) im Kanal #minikube (Einladungen gibt es [hier](http://slack.kubernetes.io/)). Wir haben auch die [kubernetes-dev Google Groups mailing list](https://groups.google.com/forum/#!forum/kubernetes-dev). Sollten Sie auf der Liste posten, fügen Sie bitte den Prefix "minikube: " zum Betreff hinzu.

{{% /capture %}}
