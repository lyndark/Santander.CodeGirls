# AWS Step Functions
O Step Functions é baseado em máquinas de estado e tarefas. As máquinas de estado são chamadas de fluxos de trabalho, que são uma série de etapas orientadas a eventos.
Cada etapa no fluxo de trabalho é chamada de estado. Por exemplo, um estado de tarefa representa uma unidade de trabalho que outro serviço executa, como chamar outro service ou API. <br>
**Serviço de orquestração serverless:** Permite criar fluxos de trabalho (workflows) compostos por etapas chamadas máquinas de estado. <br>
Cada etapa pode invocar serviços da AWS como Lambda, ECS, DynamoDB, S3, entre outros.

## Principais funcionalidades
**• Interface visual (Workflow Studio):** Permite arrastar e soltar componentes para criar fluxos de trabalho complexos sem escrever código.<br>
**• Automação de processos:** Integra mais de 220 serviços da AWS para automatizar tarefas como ETL, processamento de dados, e pipelines de machine learning.<br>
**• Execução paralela e condicional:** Suporta ramificações, loops, e execução paralela de tarefas.<br>
**• Monitoramento e rastreamento:** Fornece logs detalhados e visualização em tempo real da execução dos workflows.<br>

## Exemplo de Workflow com AWS Step Functions
Imagine que você quer processar uma imagem enviada por um usuário. O fluxo pode ser:
1. 	Receber a imagem via API Gateway
2. 	Armazenar no S3
3. 	Executar uma função Lambda para redimensionar ou aplicar filtros
4. 	Salvar o resultado em outro bucket
5. 	Enviar notificação via SNS ou e-mail
Esse fluxo pode ser modelado com Step Functions usando o seguinte diagrama de estados:

```json
{
  "StartAt": "SalvarImagem",
  "States": {
    "SalvarImagem": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:REGIAO:ID:function:SalvarImagem",
      "Next": "ProcessarImagem"
    },
    "ProcessarImagem": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:REGIAO:ID:function:ProcessarImagem",
      "Next": "EnviarNotificacao"
    },
    "EnviarNotificacao": {
      "Type": "Task",
      "Resource": "arn:aws:lambda:REGIAO:ID:function:EnviarNotificacao",
      "End": true
    }
  }
}
```

## Benefícios:
• 	Alta resiliência: cada etapa é monitorada e pode ser reexecutada em caso de falha. <br>
• 	Escalabilidade automática: adapta-se automaticamente à carga de trabalho.<br>
• 	Baixo custo operacional: modelo pay-per-use e sem necessidade de provisionar servidores.<br>
• 	Fácil integração com outros serviços AWS e aplicações externas via API Gateway e EventBridge.<br>

## Casos de uso comuns:
• 	Orquestração de pipelines de dados. <br>
• 	Execução de processos de negócios. <br>
• 	Coordenação de microserviços. <br>
• 	Automatização de tarefas administrativas. <br>
