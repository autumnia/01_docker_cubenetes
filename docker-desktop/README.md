# 명령어
## cluster
	kubectl get-cluster

## config	
	kubectl config view
	kubectl config get-clusters
	kubectl config get-contexts
	kubectl config current-context	
	kubectl config set current-context test

## namespace
	kubectl get namespace (약어: ns)
	kubectl get pod --namespace kube-system	

## node
	kubectl get nodes

## pod
	kubectl get pods -o wide
	kubectl get pods --namespace default
	kubectl apply --filename 파일명.yaml --namespace default
	kubectl run myapp2 --image=계정명/이미지명:버전 --namespace default
	kubectl get pod 파드명 --output wide --namespace default
	kubectl get pod 파드명 --output yaml --namespace default > pod.yaml
	kubectl get pod 파드명 --output jsonpath='{.spec.containers[].image}' --namespace default 
	kubectl get pod 파드명 --output json --namespace default | jq '.spec.containers[].image'  // 윈도우에서 실행 안됨

## describe
	kubectl describe pod 파드명 --namespace default

## logs
	kubectl logs 파드명 --namespace default

## label
	kubectl get pod --selector app=파드명
	kubectl logs --selector app=파드명

## debug
	kubectl debug -it 파드명 --image=계정명/이미지명:버전 --target=컨테이너명 --namespace 네임스페이스명 -- sh


## run
	kubectl run myapp2 --image=계정명/이미지명:버전 --namespace default
	kubectl --namespace default run 파드명 --image=계정명/이미지명:버전 --rm -it --restart=Never --command -- nslookup google.com


## exe
	kubectl --namespace default run 파드명 --image=계정명/이미지명:버전 --command -- /bin/sh -c "명령어"		

## port-fowarding
	kubectl port-forward 파드명 5555:8080 --namespace default	

## edit
	kubectl edit pod myapp --namespace defaul


## delete
	kubectl delete pod 파드명 --namespace default

---
---
## 연습용
	kubectl apply --filename chapter-04/myapp.yaml --namespace default	
	kubectl get pod myapp --output yaml --namespace default > pod.yaml
	kubectl get pod myapp --output jsonpath='{.spec.containers[].image}' --namespace default
	kubectl get pod myapp --output json --namespace default | jq '.spec.containers[].image' 
	kubectl get pod myapp --v=7 --namespace default
	kubectl describe pod myapp --namespace default
	kubectl logs myapp --namespace default
	kubectl debug --stdin --tty myapp --image=curlimages/curl:8.4.0 --target=hello-server --namespace default -- sh
	kubectl --namespace default run busybox --image=busybox:1.36.1 --rm -it --restart=Never --command -- nslookup google.com
	kubectl --namespace default run curlpod --image=curlimages/curl:8.4.0 --command -- /bin/sh -c "while true; do sleep infinity: done"		
	kubectl get pod myapp --output wide --namespace default
	kubectl --namespace default exec -it curlpod -- /bin/sh
	kubectl port-forward myapp 5555:8080 --namespace default	
	kubectl delete pod myapp3 --namespace default