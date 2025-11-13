# Arquitetura em Nuvem

* Um arquiteto de nuvem avalia e busca fornecer melhores práticas para a utilização dos serviços, reduzindo custos e complexidade.
* Requer uma análise sobre quais os objetivos do cliente.
* E necessário pressupor que tudo poderá falhar em algum momento.

## AWS Well-Architected Framework.
* Os pilares são: Excelência operacional, segurança, confiabilidade, eficiência de desempenho e otimização de custos (e sustentabilidade).
* Para cada pilar existem melhores práticas.

### Excelência Operacional
* O foco desse pilar é de monitorar sistemas para agregar valor comercial e melhorar os processos e procedimentos de suporte.
* Como principais tópicos ele aborda:
  * Gerenciar e automatizar alterações.
  * Responder a eventos.
  * Definir padrões para gerenciar com êxito as operações diárias.
* Princípios de design do pilar:
  * Executar operações como código (pois evita erros humanos).
  * Anotar a documentação.
  * Fazer alterações fraquentes, pequenas e reversíveis.
  * Refinar procedimentos operacionais com frequência.
  * Prever falhas.
  * Aprender e compartilhar.
* Preparação, execução e evolução.

### Segurança
* O foco dese pilar é em proteger informações, sistemas e ativos, e ao mesmo tempo agregar valor comercial por meio de avaliações de risco e estratégias de mitigação.
* Como principais tópicos, ele aborda:
  * Identificar e gerenciar quem pode fazer o quê.
  * Estabelecimento de controles para detectar eventos de segurança.
  * Proteção de sistemas e serviços.
  * Confidencialidade e integridade dos dados.
* Princípios de design do pilar:
  * Implementar uma base de identidade sólida (least privileged).
  * Habilitar a rastreabilidade.
  * Aplicar segurança em todas as camadas.
  * Automatizar as melhores práticas de segurança.
  * Proteger dados em trânsito e ociosos.
  * Manter as pessoas longe dos dados.
  * Preparar-se para eventos de segurança.
* Identity and access management, controles de detecção, proteção de infraestrutura, proteção de dados e reposta a incidentes.

### Confiabilidade
* O foco desse pilar é em previr e recuperar rapidamente de falhas para atender à demanda dos negócios e dos clientes.
* Como principais tópicos, ele aborda:
  * Configuração.
  * Requisitos entre projetos.
  * Planejamento de recuperação.
  * Tratamento de alterações.
* Princípios de design do pilar:
  * Testar procedimentos de recuperação.
  * Recuperar-se automaticamente de falhas.
  * Escale horizontalmente para aumentar a disponibilidade do sistema.
  * Pare de tentar adivinhar a capacidade.
  * Gerenciar alterações na automação.
* Fundamentos, gerenciamento de alterações e gerenciamento de falhas.

### Eficiência de Performance
* O foco desse pilar é em usar os recursos de computação de forma eficiente para atender aos requisitos do sistema, mantendo a eficiência a medida que existem mudanças na demanda e as tecnologias evoluem.
* Como principais tópicos, ele aborda:  
  * Seleção dos tipos e tamanhos certos de recursos com base nos requisitos de carga de trabalho.
  * Monitoramento e desempenho.
  * Tomar decisões embasadas para manter a eficiência à medida que as necessidades empresariais evoluem.
* Princípios de design do pilar:
  * Democratizar tecnologias avançadas.
  * Tenha alcance global em minutos.
  * Usar arquiteturas sem servidor.
  * Experimentar com mais frequência (testar e comparar).
  * Ter afinidade mecânica.
* Seleção, revisão, monitoramento e vantagens e desvantagens.

### Otimização de Custos
* O foco desse pilar é em executar sistemas para agregar valor comercial pelo menor preço.
* Como principais tópicos temos:
  * Compreender e controlar quando o dinheiro está sendo gasto.
  * Selecionar o número mais apropriado e correto de tipos de recursos.
  * Analisar gastos ao longo do tempo.
  * Escalabilidade para atender às necessidades empresariais sem gastos excessivos.
* Princípios de design do pilar:
  * Adotar um modelo de consumo.
  * Medir a eficiência geral.
  * Eliminar despesas em operações de datacenter.
  * Analisar e atribuir despesas.
  * Usar serviços gerenciados e em nível de aplicativo para reduzir o custo de propriedade.
* Visibilidade de gastos, recursos de baixo custo, correspondência de oferta e demanda, otimização ao longo do tempo.

## Confiabilidade e Alta Disponibilidade
* A confiabilidade é uma medida da capacidade do sistema de fornecer funcionalidade quando o usuário quiser.
  * O sistema inclui o hardware, firmware e software.
* Tempo médio entre falhas (MTBF) = tempo total em serviço/número de falhas.
* Existem métricas de confiabilidade.
* A disponibilidade é o tempo normal de operação/tempo total.
* A disponibilidade costuma ser calculada no período de um ano.
  * Número de noves, ou seja, 5 noves = 99,999% de disponibilidade.
* Níveis de disponibilidade.
* Fatores que influenciam a disponibilidade:
  * Tolerância a falhas.
  * Escalabilidade.
  * Capacidade de recuperação.

## AWS Trusted Advisor
* Uma ferramenta que fornece orientações em tempo real para ajudar a provisionar os recursos de acordo com as melhores práticas da AWS.
* Examina todo o ambiente da AWS, oferecendo recomendações em cinco categorias: custos, desempenho, segurança, tolerância a falhas e limites de serviços.
* Da pra fazer a análise antes mesmo de ter tudo pronto.