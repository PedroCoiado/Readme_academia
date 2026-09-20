# Entrega 1 - Modelo Conceitual (DER)

**Sistema de Gestão de Informações para Academia de Artes Marciais**

## Metadados

* **Nome do Aluno 1:** Nickolas Henrique Bezerra - **RGM:** 47685778
* **Nome do Aluno 2:** Pedro Henrique Ruola Coiado - **RGM:** 47589124
* **Nome do Aluno 3:** Raphaela Gonçalves Neves - **RGM:** 47656166
* **Nome do Aluno 4:** Williams Vargas Neves Paoli dos Santos - **RGM:** 47336820
* **Professor/Disciplina:** Cid Rodrigues De Andrade - Modelagem de Banco de Dados

\---

## 1\. Caracterização da Organização

* **Nome e natureza da organização:** Base Forte Leste - Academia de Artes Marciais (Gerida pelo CEO Adalberto). É uma organização com fins lucrativos voltada para a prestação de serviços esportivos e ensino de lutas.
* **Contexto e porte:** Organização de pequeno porte. A academia oferece 6 modalidades (Muay Thai, Kickboxing, Jiu-Jitsu, Boxe, Capoeira e No-Gi). As turmas são divididas por horários e possuem um limite de até 30 alunos por turma.
* **Problemas e necessidades identificados:** Atualmente, a academia enfrenta uma crise operacional devido ao uso exclusivo de fichas de papel e tratativas informais pelo WhatsApp. Os principais problemas são: atrasos recorrentes no pagamento das mensalidades (que vencem todo 5º dia útil e os atrasos não são registrados), total falta de controle sobre a frequência/presença dos alunos e dificuldade para rastrear o tempo de treino real para exames de faixa.
* **Justificativa da escolha:** A organização foi escolhida pela facilidade de acesso ao gestor (CEO Adalberto) e por ser um cenário perfeito para iniciantes em banco de dados: possui regras de negócio claras e uma necessidade urgente de centralização de dados para resolver problemas financeiros e operacionais.
* **Evidências da organização:**

  * *Entrevista de Campo:* Realizada presencialmente em 01/09/2026 pelo aluno Nickolas Henrique Bezerra com o CEO Adalberto.
  * *Endereço e Contato:* \[Inserir o endereço real da academia aqui e o link do Google Maps/Instagram, se houver].

\---

## 2\. Processos de Negócio

Mapeamos os três principais fluxos de funcionamento da academia com base na entrevista:

* **Processo de Cadastro e Matrícula:** O aluno preenche uma ficha física de papel com seus dados. A data da matrícula é anotada nessa ficha. Não existe um número de matrícula gerado, a identificação é feita apenas pelo nome/CPF.
* **Processo de Mensalidade:** A academia trabalha com os planos Mensal, Trimestral, Anual e Família. O vencimento é fixo (todo 5º dia útil). O controle é feito de forma manual pelo WhatsApp, registrando apenas a data em que o aluno pagou.
* **Processo de Graduação e Frequência:** Atualmente, a presença nas aulas **não é registrada** de forma alguma. No entanto, a frequência deveria influenciar diretamente na elegibilidade para os exames de faixa (nas modalidades que possuem faixa) ou na análise técnica (como no Boxe). A evolução hoje depende da percepção visual do professor.

\---

## 3\. Requisitos do Sistema

### 3.1 Requisitos Funcionais (O que o sistema deve fazer)

* **RF01:** O sistema deve permitir o cadastro de alunos salvando nome, CPF, idade, tipo sanguíneo, histórico de treinos anteriores e situação (Ativo, Inativo ou Trancado).
* **RF02:** O sistema deve permitir o cadastro de professores e instrutores, vinculando cada um à sua respectiva modalidade.
* **RF03:** O sistema deve permitir o cadastro de turmas, definindo a modalidade, os dias/horários das aulas e associando um professor e um instrutor responsável.
* **RF04:** O sistema deve registrar os pagamentos das mensalidades, identificando o plano escolhido (mensal, trimestral, anual ou família) e a data do pagamento.
* **RF05:** O sistema deve registrar a frequência diária (presença) dos alunos nas aulas.
* **RF06:** O sistema deve permitir o registro do histórico de graduações e exames de faixa dos alunos com suas respectivas datas.

### 3.2 Requisitos Não Funcionais (Características de qualidade)

* **RNF01 (Integração):** O banco de dados deve ser estruturado de forma a permitir uma futura integração com um sistema de catraca por reconhecimento facial.
* **RNF02 (Segurança):** O sistema deve garantir a privacidade dos dados sensíveis dos alunos (como CPF e Tipo Sanguíneo).
* **RNF03 (Vencimento Fixo):** Toda mensalidade possui como data padrão de vencimento o quinto dia útil de cada mês.
* **RNF04 (Limite de Alunos):** Uma turma não pode ultrapassar o limite máximo de 30 (trinta) alunos matriculados.
* **RNF05 (Exclusividade do Professor):** Um professor só pode ser associado e ministrar aulas na modalidade em que possui propriedade/especialização.
* **RNF06 (Trancamento por Lesão):** O aluno pode alterar seu status para "Trancado" caso sofra uma lesão, interrompendo temporariamente a cobrança ou contagem de tempo.

\---

## 4\. Regras de Negócio (Restrições e regras de funcionamento)

(A adicionar).

\---

## 5\. Dicionário de Dados Conceitual (Preliminar)

Abaixo está o dicionário de dados completo, com todas as entidades e atributos que constam no Diagrama Entidade-Relacionamento (Seção 7):


\---

## 6\. Modelagem Conceitual

### Entidades reconhecidas e justificativas:

* **ALUNO:** Necessária para armazenar os dados pessoais, técnicos e a situação cadastral de quem treina.
* **PROFESSOR / INSTRUTOR:** Registra quem ministra as aulas. Importante para o controle de turmas (já que cada turma tem um professor e um instrutor).
* **TURMA:** Entidade que organiza o cronograma de aulas, limitando a 30 alunos e vinculando a modalidade e os horários.
* **PAGAMENTO:** Entidade essencial para resolver o problema de inadimplência, registrando as datas de pagamento e os planos.
* **PRESENCA:** Criada para suprir a necessidade de controle de frequência, registrando os dias em que o aluno treinou para fins de graduação.

### Relacionamentos principais:

* **ALUNO possui PAGAMENTO (1,1 para 0,N):** Um pagamento pertence a um único aluno. Um aluno terá vários pagamentos ao longo do tempo.
* **PROFESSOR e INSTRUTOR regem TURMA (1,1 para 0,N):** Cada turma precisa de um professor e um instrutor responsáveis.
* **TURMA possui ALUNOS (1,N para 0,N):** Uma turma tem vários alunos (máximo 30) e um aluno pode participar de mais de uma turma/modalidade.

\---

## 7\. Diagrama Entidade-Relacionamento (DER)
!\[Diagrama Entidade Relacionamento]<img width="1269" height="765" alt="diagrama" src="https://github.com/user-attachments/assets/8fdb0a65-903a-4281-bb04-a3f3ea9534f3" />


\---

## 8\. Justificativa Técnica

Como o grupo é iniciante na disciplina, optamos por uma abordagem direta e focada nos problemas críticos relatados pelo CEO Adalberto: mensalidades e frequência. Criamos a entidade **PRESENCA** separada do **ALUNO** porque mapeamos que a frequência é o dado que o professor precisa para avaliar a troca de faixa. Se guardássemos apenas a "última presença" no cadastro do aluno, a academia continuaria sem o histórico necessário para os certificados de graduação. A separação das entidades garante que o banco de dados resolva a desorganização atual sem inflar a complexidade do modelo nesta primeira entrega.

\---

## 9\. Uso de Inteligência Artificial

*(Documentação obrigatória sobre o uso da IA para organizar o trabalho)*.

|Ferramenta e etapa|Motivação|Prompt(s) utilizados / Resposta recebida|Fontes consultadas|Trechos rejeitados/corrigidos|Justificativa da escolha final|Reflexão crítica|
|-|-|-|-|-|-|-|
|**ChatGPT** na organização do README.|Estruturar os dados brutos da entrevista de campo no formato do template exigido.|*Prompt:* "Ajuste o template com base no questionário da academia..."|Questionário de Levantamento de Requisitos preenchido pelo grupo.|Foram removidas sugestões automáticas da IA que envolviam módulos complexos de vendas de produtos (como suplementos), focando apenas no que o CEO pediu (presença e mensalidade).|Mantivemos a estrutura simples para atender estritamente o escopo pedido pelo professor sem complicar a entrega do grupo iniciante.|A IA ajudou a converter as respostas da entrevista em requisitos formais rapidamente, mas a validação humana foi necessária para manter o projeto realista.|



