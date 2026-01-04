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