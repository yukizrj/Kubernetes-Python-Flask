# Kubernetes-Python-Flask
run a Kubernetes Flask Microservice that returns the correct amount of change locally on your desktop machine

## how to deploy app to Kubernetes through Docker
1. download:
Docker Desktop

2. install:
	pip install --upgrade pip
	pip install -r requirements.txt

3. test(optional):
	python -m pytest -vv --cov=app test_app.py

4. build:
	docker build -t flask-change:latest .
    To verify container: `docker image ls`

5. run:
	docker run -p 8080:8080 flask-change

6. invoke:
	curl http://127.0.0.1:8080/change/1/34
    or test in browser

7. run-kube:
	kubectl apply -f kube-hello-change.yaml
    To verify Kubernetes is working: `kubectl get nodes`
    To verify container is running: `kubectl get pods`
    To describe the load balanced service: `kubectl describe services hello-flask-change-service`

8. cleanup the deployment:
    kubectl delete deployment hello-python
