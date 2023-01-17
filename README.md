cd templates

kubectl create deployment web1 --image=nginx --dry-run=client -o yaml > deployment.yaml
kubectl expose deployment web1 --port=80 --target-port=80 --type=NodePort --dry-run=client -o yaml > service.yaml

PS: if you want to create service.yaml, need to create a real deployment first, like: "kubectl create deployment web1 --image=nginx"


# 然后要回到整个 mychart 的目录下面 (就是说回到包含这个整个目录的文件夹下面)
chengxun@hp:~/workspace/k8s/mychart/templates$ cd ..
chengxun@hp:~/workspace/k8s/mychart$ cd ..
chengxun@hp:~/workspace/k8s$ helm install web1 mychart/

# 如果后来改了 yaml 文件，那么就运行
helm upgrade web1 mychart
helm uninstall web1