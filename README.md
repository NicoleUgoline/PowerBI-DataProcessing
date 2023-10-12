# PowerBI-DataProcessing
## Descrição
O projeto "Processando e Transformando Dados com PowerBI" é uma iniciativa dedicada a explorar as capacidades avançadas de transformação e análise de dados oferecidas pela plataforma PowerBI. O objetivo é demonstrar como o PowerBI pode ser uma ferramenta poderosa para processar e refinar dados brutos, convertendo-os em insights valiosos e visuais informativos.

## Etapas Aplicadas:
- Renomeação de Colunas: Inicialmente, as colunas foram renomeadas visando aprimorar a legibilidade dos dados, facilitando tanto a interpretação humana quanto a utilização eficaz em elementos gráficos.
- Padronização de Valores Monetários: Foi realizada uma modificação nos valores monetários, convertendo-os para o formato decimal fixo. Essa padronização torna a manipulação e análise mais consistente.
- Tratamento de Valores Null: Os valores nulos presentes na coluna "super_ssn" foram substituídos por "no supervisor". Essa ação foi tomada porque esses valores indicam que um empresário é um gerente sem um supervisor direto.
- Correção do Campo de Endereço: O campo "address" foi dividido usando o delimitador "-", com uma correção específica para um registro que gerou uma coluna adicional com um valor único. Esse ajuste foi acompanhado da devida renomeação.
- Gestão de Departamentos sem Gerente: Foi identificado que alguns departamentos não possuíam um gerente associado. Essa observação é crucial para compreender a estrutura da organização.
- Análise Específica para Funcionário sem Horas no Projeto: Foi notado que o funcionário "James" não possuía horas registradas no projeto. Esse caso excepcional pode ser atribuído à sua função gerencial sem envolvimento direto no desenvolvimento do projeto.
- Separação da Coluna de Endereço: A coluna "Endereço" na tabela de funcionários foi separada, possivelmente para uma melhor organização dos dados e facilitar futuras consultas relacionadas ao endereço.
- Consulta de Recuperação de Encarregado e Gerente:
Foi implementada uma consulta SQL que recupera os nomes do encarregado e seu respectivo gerente. Isso é valioso para entender a hierarquia e as relações dentro da organização

```sql
SELECT
e.Fname || ' ' || COALESCE(e.Minit || '. ', '') || e.Lname AS "EmployeeName",
m.Fname || ' ' || COALESCE(m.Minit || '. ', '') || m.Lname AS "MgrName"
FROM azure_company.employee e
INNER JOIN azure_company.employee m ON e.Super_ssn = m.Ssn;
```
## Observações sobre o Processamento dos Dados no Power BI:
- A ação de mesclagem no Power BI é semelhante a juntar dados em colunas com base nas correspondências, enquanto o 'Atribuir' concatena as linhas de forma mais desestruturada. Ao mesclar os nomes de departamentos e localizações, criamos combinações únicas, onde cada departamento associado a uma localização é uma entidade distinta. Isso é crucial para criar visualizações distintas, facilitando análises e relatórios precisos e claros. O uso do 'Atribuir' não proporcionaria essa organização distintiva, podendo dificultar a visualização e análise dos dados.
- Os dados e consultas são fictícios e destinados apenas para fins de aprendizagem.
- Os dados utilizados neste projeto foram extraídos e processados a partir do banco de dados PostgreSQL integrado com a Azure.

