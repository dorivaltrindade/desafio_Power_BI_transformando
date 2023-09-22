#### **DESAFIO DE PROJETO**
## **Processamento de Dados Simplificado com Power BI**
#### *Módulo - Visualização e Análise de Dados com Power BI*
##### **Santander Bootcamp 2023 - Ciência de Dados com Python - Digital Inovation One - DIO**
---- 
#### **ATIVIDADES REQUERIDAS**

## 

- **Criação de uma instância na Azure para banco de dados MySQL**
https://github.com/dorivaltrindade/desafio_Power_BI_transformando/blob/main/01_instancia_azure.png
---- 
https://github.com/dorivaltrindade/desafio_Power_BI_transformando/blob/main/02_instancia_azure_MySQL.png

- **Banco de dados MySQL criado na instância Azure e alimentado conforme os scripts encontrados no seguinte repositório GitHub:**

##### [Power BI Analyst - Mod.3 - Desafio de Projeto (owner: Juliana Azanelatto)](https://github.com/julianazanelatto/power_bi_analyst/tree/main/M%C3%B3dulo%203/Desafio%20de%20Projeto)


- **Integração do Power BI com MySQL na instância Azure**
https://github.com/dorivaltrindade/desafio_Power_BI_transformando/blob/main/03_Integracao_MySQL_Workbench%20x%20Azure.png
----
https://github.com/dorivaltrindade/desafio_Power_BI_transformando/blob/main/04_Integracaoo_Power_BI%20x%20Azure.png
- **Qualidade dos dados** (qualidade/distribuição das colunas)
---
##### (verificação de problemas na base de dados que necessitam da transformação dos dados)
Para melhorar a constatação da origem dos dados na nuvem, foi adotado o nome do esquema (***Schema***) como ***azure_company***, ou seja, o prefixo de identificação das tabelas do banco de dados é ***azure_company***.

Antes da execução dos scripts para criação das tabelas e alimentaçãos dos respectivos dados no MySQL foram corrigidas todas ocorrências da expressão **"departament"** para o Inglês correto, **"department"**. Com relação a consistência dos dados (distintos e exclusivos), conforme a observação da figura a seguir, todos os dados foram aceitos com 0% de erros, 0% vazios e 100% válidos em todas as tabelas importadas.

https://github.com/dorivaltrindade/desafio_Power_BI_transformando/blob/main/05_Qualidade_dos_Dados.png


O processo de melhorias nos dados da base e possíveis correções transcorrerá conforme as diretrizes para transformação dos dados na ordem a seguir:

#### **01 - Adequação de *cabeçalhos* e *tipos de dados* das tabelas:**

- department - *nenhuma alteração foi necessária*
- dependent - *nenhuma alteração foi necessária*
- dept_locatíons - *nenhuma alteração foi necessária*
- employee - *coluna salário, tipo de dado modificado para {{"Salary", Currency.Type}}*
- project - *nenhuma alteração foi necessária*
- works_on - *nenhuma alteração foi necessária*
---
#### **02 - Modificação dos valores monetários para o tipo double precision**

- A alteração da coluna **salary** da tabela **employee** para ***currency type*** não altera a precisão interna dos números para efeito de cálculos.
---
#### **03 - Verificação da existência dos nulos e analise a remoção**

- A única ocorrência de nulo (*null*) refere-se ao funcionário ***James*** que não possui gerente indicado na coluna ***Super_ssn*** da tabela ***employee***.
---
#### **04 - Verificação de colaborador sem gerente**

- A não indicação de gerente para o colaborador ***James*** (employee.Fname) é coerente porque ele não será gerente de si mesmo.
---
#### **05 - Verificação de departamento sem gerente**

- Não há ocorrência de departamentos sem gerente (department.Mgr_ssn).
---
#### **06 - Tratativa para departamento sem gerente**

- Não há necessidade de indicar o código de gerente para a coluna *Mgr_ssn* na tabela de *department*.
---
#### **07 - Verificalção do número de horas dos projetos**

- Todos os projetos cadastrados (*project.Pnumber*) possuem horas trabalhadas em *works_on.Hours*.
---
#### **08 - Separação de colunas complexas**

- Na tabela *employee*, foi corrigida a expressão "Fire-Oak" para "Fire Oak" da coluna *Address*, via recurso substituir valores a fim de permitir Dividir Coluna, usando o separador "**-**".
- Foram desmembrados os elementos da coluna *Address *da tabela *employee*, resultando em quatro outras distintas: ***Houseno***, ***Street***, ***City*** e ***State***.
---
#### **09 - Mesclagem da consultas employee  e department** 

- Criada a consulta ***employee_dept*** com o nome dos departamentos associados aos colaboradores.
---
#### **10 - Eliminação das colunas desnecessárias em employee_dept.**

- As colunas desnecessárias da nova consulta mesclada, ***employee_dept***, foram removidas.
---
#### **11 - Junção dos colaboradores e respectivos gerentes**

- Criada a consulta mesclada ***employee_manager*** por meio do recurso *Mesclar Consultas como Novas*.
---
#### **12 - Junção das colunas Nome e Sobrenome da tabela *employee***

- Inserida a coluna FullName por meio do *Mesclar Colunas* com o uso do separador espaço em branco.
---
#### **13 - Mesclagem das colunas nomes de departamentos e localização**

- Criada a consulta mesclada Dept_Local na tabela ***dept_locations*** por meio do recurso *Mesclar Consultas*.
---
#### **14 - Explicação do porquê mesclar e não o atribuir (item 13).**

- A mesclagem é a opção correta visto que a atribuição refere-se a inserção de novos valores. Na solicitação do item 13, bastou combinar dados pré-existentes das colunas das consultas envolvidas.
---
#### **15 - Contagem de colaboradores por gerente**

- Para realizar a contagem, foi necessário criar a nova consulta mesclada, ***manager_employee***.
---
#### **16 - Elimine as colunas desnecessárias, que não serão usadas no relatório, de cada tabela**

- A eliminação das colunas desnecessária exigiu cautela tendo em vista a possível quebra de sustenção dos relacionamentos entre várias consultas.
---
---
O passo a passo das operações realizadas pode ser comprovado, examinando-se o arquivo desafio-projeto-bc-dio-dorival-azure_company.pbix .

Arquivo publicado: https://app.powerbi.com/groups/me/datasets/8d3547cf-b6e0-41c4-add5-2cae201f7d4c/details?experience=power-bi
