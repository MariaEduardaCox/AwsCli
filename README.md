# AwsCli
Teste de comandos para criar uma tabela no aws cli.

aws dynamodb create-table --table-name minha-tabela --attribute-definitions AttributeName=id,AttributeType=S AttributeName=nome,AttributeType=S --key-schema AttributeName=id,KeyType=HASH AttributeName=nome,KeyType=RANGE --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5

aws dynamodb put-item --table-name minha-tabela --item '{"id": {"S": "1"}, "nome": {"S": "John Doe"}}'

aws dynamodb update-table --table-name minha-tabela --attribute-definitions AttributeName=id,AttributeType=S --global-secondary-index-updates '[{"Create":{"IndexName":"meu-indice-global","KeySchema":[{"AttributeName":"id","KeyType":"HASH"}],"Projection":{"ProjectionType":"ALL"},"ProvisionedThroughput":{"ReadCapacityUnits":5,"WriteCapacityUnits":5},"Action":"CREATE"}}]'

aws dynamodb query --table-name minha-tabela --key-condition-expression "id < :id" --expression-attribute-values '{":id":{"S":"10"}}'

aws dynamodb query --table-name minha-tabela --key-condition-expression "id > :id" --expression-attribute-values '{":id":{"S":"10"}}'
