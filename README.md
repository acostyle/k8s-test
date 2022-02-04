# K8S test

K8S for learning purposes

# Minikube development setup


- Install [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
- Install [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- Install [Kubectl](https://kubernetes.io/docs/tasks/tools/)

- Start Minikube cluster in VirtualBox environment

```
minikube start --vm-driver=virtualbox
```

- Install [Helm](https://helm.sh/)

- Install Helm Chart for postgresql

```
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install my-release bitnami/postgresql
```

- Create a Postgres database

- Clone the repository and go inside cloned repo

```bash
git clone git@github.com:acostyle/k8s-test.git
```

```bash
cd k8s-test
```

- Add your env variables to `django-config.yaml`


## Run next commands
- ```kubectl apply -f django-config.yaml ```
- ```kubectl apply -f django-deployment.yaml ```
- ```kubectl apply -f django-ingress.yaml ```
- ```kubectl apply -f django-migrate.yaml```
- ```kubectl apply -f django-clearsessions.yaml ```

Then create superuser for Django. You can get your POD name via ```kubectl get pods```:
```
kubectl exec <POD_NAME> -it -- bash
```
```
python3 ./manage.py createsuperuser
```

Don't forget to add in '/etc/hosts' file next line:
```
echo "$(minikube ip) star-burger.test" | sudo tee -a /etc/hosts
```