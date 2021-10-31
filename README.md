# Passado a passo

1. Criar tag para a imagem desejada em conformidade com o container registry
```
docker tag image-desejada:versao nome-do-container-registry/imagem-desejada:versao
```
2. Autenticar no registry
```
docker login registry-prodiver-com/registry-nome
```

3. Enviar a imagem para o container registry
```
docker push nome-do-container-registry/imagem-desejada:versao
```

4. Criar secrets por linha de comando (opcional)
```
kubectl create secret docker-registry registry-secret --docker-server=<registry-name> --docker-username=<username> --docker-password=<password> --docker-email=<user@email.com>
```

5. Aplicar manifestos no cluster kubernetes
```
kubectl apply -f ./k8s
```

## Observações
1. No Azure não funcionou utilizando as `secrets` por manifesto. Preciso verificar o que houve.
2. Na digital ocean há uma facilidade de integração do cluster com o registry. É possível dar permissões de leitura pelo próprio painel. Caso precise de algo mais refinado será necessário mapear por meio de `secrets`.