
# Kubernetes: Criando, Acessando e Gerenciando Pods

## 1. Aplicando o Arquivo YAML no Kubernetes

Para iniciar a criação de um pod no Kubernetes usando um arquivo YAML, basta executar o seguinte comando:

```bash
kubectl apply -f <pod-name.yaml>
```

Isso vai aplicar a configuração descrita no arquivo ao seu cluster Kubernetes.

## 2. Verificando a Criação do Pod

Depois de aplicar o arquivo, você pode verificar se o pod foi criado corretamente com o comando:

```bash
kubectl get pods
```

Se tudo ocorrer bem, o pod aparecerá na lista com o status `Running`.

## 3. Acessando o Pod (Nginx) via Port-Forwarding

Se o seu pod estiver rodando uma aplicação como o Nginx, você pode redirecionar uma porta do seu computador local para o pod. Use o seguinte comando:

```bash
kubectl port-forward pod/<pod-name> 8080:80
```

Isso vai redirecionar a porta 8080 do seu host local para a porta 80 do contêiner Nginx que está rodando no pod.

- **Para acessar no navegador**: Abra seu navegador e digite:

  ```
  http://localhost:8080
  ```

Se tudo estiver funcionando corretamente, você verá a página padrão do Nginx.

## 4. Escalando um Deployment

Uma das grandes vantagens do Kubernetes é a facilidade em escalar suas aplicações. Para aumentar o número de réplicas de um deployment — por exemplo, para 5 réplicas — execute o seguinte comando:

```bash
kubectl scale deployment <deployment-name> --replicas=5
```

Com isso, o número de pods em execução será aumentado para 5, proporcionando mais resiliência e disponibilidade à sua aplicação.

## 5. Deletando Recursos do Kubernetes

### Deletando um Pod

Para remover um pod específico, utilize:

```bash
kubectl delete pod <pod-name>
```

Esse comando irá deletar o pod do cluster.

### Deletando um Deployment (e os Pods associados)

Se você quiser remover um deployment junto com todos os pods que ele gerencia, faça o seguinte:

```bash
kubectl delete deployment <deployment-name>
```

Dessa forma, o deployment e todos os pods relacionados serão removidos do cluster.

### Verificando o Status da Atualização

Para acompanhar o progresso de uma atualização em um deployment, você pode usar:

```bash
kubectl rollout status deployment/nginx-deployment
```

### Desfazendo uma Atualização de Deployment (Rollback)

Caso precise reverter uma atualização, o comando a ser utilizado é:

```bash
kubectl rollout undo deployment/nginx-deployment
```

