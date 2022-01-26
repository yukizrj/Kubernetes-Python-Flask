# Kubernetes-Python-Flask
run a Kubernetes Flask Microservice that returns the correct amount of change locally on your desktop machine

## how to deploy app to Kubernetes through Docker
1. download:
  Docker Desktop<br />

2. install:
  pip install --upgrade pip<br />
  pip install -r requirements.txt<br />

3. test(optional):
  python -m pytest -vv --cov=app test_app.py<br />

4. build:
  docker build -t flask-change:latest .<br />
  To verify container: `docker image ls`<br />

5. run:
  docker run -p 8080:8080 flask-change<br />

6. invoke:
  curl http://127.0.0.1:8080/change/1/34<br />
  or test in browser<br />

7. run-kube:
  kubectl apply -f kube-hello-change.yaml<br />
  To verify Kubernetes is working: `kubectl get nodes`<br />
  To verify container is running: `kubectl get pods`<br />
  To describe the load balanced service: `kubectl describe services hello-flask-change-service`<br />

8. cleanup the deployment:
  kubectl delete deployment hello-python<br />
