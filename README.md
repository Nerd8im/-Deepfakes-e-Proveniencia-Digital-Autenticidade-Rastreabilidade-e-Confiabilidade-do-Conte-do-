
# Dossiê 4: Deepfakes e Proveniência de Conteúdo

## Integrantes

| Nome completo | RGM | GitHub | Área de carreira |
|---|---|---|---|
| Albert dos Santos Mariano| 47857927 | AlbertdosSantosMariano | Engenharia de Dados
| Gabriel Anjos Albuquerque | 48037931 | Nerd8im | Engenharia de Dados
| João Pedro Theodoro de Sousa Andrade| 47863251 | jp-theodoro | Ciência de Dados 
| Petterson Michel Lima Aguilar | 47859792 | PettersonAguilar | Engenharia de Dados
| Samuel Carmoni de Oliveira | 47813733 |carmonisamuel-cloud | Cybersegurança
|---|---|---|---|

### Apresentação do projeto

A evolução da inteligência artificial generativa tornou possível produzir áudios e vídeos sintéticos capazes de simular falas, aparências e comportamentos de pessoas reais. Essa tecnologia apresenta aplicações legítimas, mas também pode ser utilizada para fraudes, manipulação de informações e desinformação.

O Dossiê 4 propõe investigar como identificar conteúdos manipulados e verificar sua origem, considerando limitações tecnológicas, riscos éticos e impactos sociais.

**Recorte proposto:** Verificação de áudios e vídeos de caráter político-eleitoral compartilhados em redes sociais e aplicativos de mensagens no Brasil.

**Justificativa do recorte:** A circulação rápida desses conteúdos pode dificultar a verificação antes que uma informação falsa produza impactos sociais. O problema exige combinar Ciência de Dados, Cibersegurança, Engenharia de Dados, Computação em Nuvem e mecanismos de revisão humana.

**Proposta inicial:** Desenvolver conceitualmente o VerificaBR, uma plataforma de verificação assistida que combina análise de proveniência digital, detecção probabilística de manipulações, comparação com checagens anteriores e revisão humana.

**Pergunta central:**

> É melhor detectar o conteúdo falso ou comprovar a origem do verdadeiro? Como agir quando a tecnologia não consegue determinar a autenticidade com segurança?


## 1. Análise do problema

**Responsável:** Gabriel Anjos Albuquerque

### 1.1 Quem é afetado, onde e quanto?

Os deepfakes podem afetar diferentes grupos sociais, especialmente quando são utilizados para simular declarações, divulgar acontecimentos inexistentes ou manipular a percepção pública.

**Grupos potencialmente afetados:**

- Eleitores expostos a conteúdos políticos manipulados.
- Pessoas idosas e usuários com menor familiaridade digital.
- Jornalistas e profissionais de checagem.
- Pessoas que tiveram imagem ou voz falsificadas.
- Plataformas digitais e aplicativos de mensagens.
- Instituições públicas, incluindo a Justiça Eleitoral.

**Contexto brasileiro:**

Um levantamento de 2026 da Data Privacy Brasil e do Aláfia Lab registrou 413 casos de uso de inteligência artificial em publicações políticas entre janeiro e agosto de 2026, incluindo 336 envolvendo manipulações de imagem ou áudio de pessoas públicas.

Fonte: [Data Privacy Brasil — IA na pré-eleição de 2026](https://www.dataprivacybr.org/documentos/ia-na-pre-eleicao-deepfakes-desinformacao-e-novos-desafios-para-a-integridade-das-eleicoes-de-2026/).

Esses números correspondem ao monitoramento citado, não a uma estimativa de todos os deepfakes existentes no país.

**[PESQUISAR — RESPONSÁVEL]**

- Acrescentar pelo menos dois exemplos documentados no Brasil.
- Apresentar dados quantitativos recentes com fontes.
- Explicar a população observada e as limitações dos levantamentos.
- Descrever consequências sociais, econômicas ou institucionais.
- Relacionar o problema com o recorte escolhido.

**Texto a desenvolver:**

[Inserir análise própria do integrante, com dados e referências.]

### 1.2 Quais são as causas técnicas do problema?

A produção de conteúdos sintéticos tornou-se mais acessível com o avanço dos modelos generativos de áudio e vídeo.

Entre as principais dificuldades técnicas estão:

1. Modelos de síntese de voz e imagem cada vez mais convincentes.
2. Compartilhamento rápido de conteúdos sem verificação prévia.
3. Perda de metadados durante compressão, edição e reenvio.
4. Ausência de adoção universal de padrões de proveniência.
5. Limitações de generalização dos detectores automáticos.
6. Possíveis diferenças de desempenho entre sotaques, idiomas e condições de gravação.

Um estudo denominado *Deepfake-Eval-2024*, divulgado em 2025, mostrou que o desempenho de detectores pode cair consideravelmente quando são avaliados em conteúdos reais encontrados na internet, em comparação com bases acadêmicas tradicionais.

Fonte: https://doi.org/10.48550/arXiv.2503.02857

**[DESENVOLVER — RESPONSÁVEL]**

Explicar tecnicamente:

- Como funcionam deepfakes de voz e vídeo.
- O que são falsos positivos e falsos negativos.
- Por que um detector pode falhar em situações reais.
- Como compressão e reenvio afetam a análise.
- Quais riscos existem para conteúdos em português brasileiro.

### 1.3 O que já existe e por que não basta?

| Solução existente | O que faz | Limitação a investigar |
|---|---|---|
| Detectores de deepfake | Identificam sinais estatísticos de manipulação | Podem errar em conteúdos não vistos no treinamento |
| C2PA / Content Credentials | Permite verificar informações assinadas sobre origem e histórico de arquivos | Nem todo conteúdo possui credenciais; sua ausência não comprova falsidade |
| Agência Lupa | Realiza checagens jornalísticas | A análise humana exige tempo e recursos |
| Aos Fatos | Investiga informações e conteúdos suspeitos | Não cobre necessariamente todo conteúdo que circula |
| Sistemas de moderação | Aplicam políticas das plataformas | Podem apresentar falta de transparência ou decisões contestáveis |

**[PESQUISAR — RESPONSÁVEL]**

- Comparar pelo menos três iniciativas com referências.
- Explicar por que nenhuma resolve integralmente o recorte.
- Identificar a oportunidade de melhoria.
- Diferenciar autenticidade técnica de veracidade da informação.

**Conclusão preliminar:**

A solução proposta não deve substituir a verificação jornalística nem tratar classificações automáticas como provas definitivas. Seu objetivo é reunir evidências para apoiar uma avaliação mais transparente.

---

## 2. Proposta tecnológica

**Responsável:** Gabriel Anjos Albuquerque

### 2.1 Como o usuário utilizaria a solução?

**Nome provisório:** VerificaBR.

**Objetivo:** oferecer uma plataforma acessível para análise assistida de áudios e vídeos suspeitos.

**Fluxo proposto:**

1. O usuário acessa a plataforma.
2. Envia um arquivo de áudio ou vídeo, ou informa um link compatível.
3. A plataforma informa as condições de privacidade e solicita a confirmação necessária.
4. O sistema verifica a existência e a validade de credenciais de proveniência.
5. Um módulo analisa possíveis sinais de manipulação.
6. O sistema pesquisa conteúdos semelhantes em uma base de checagens.
7. As evidências são reunidas em um relatório compreensível.
8. Casos inconclusivos ou de maior risco são encaminhados para revisão humana.
9. O usuário recebe o resultado e pode solicitar reavaliação.

**Estados possíveis do resultado:**

- Proveniência verificada, com descrição do que foi efetivamente comprovado.
- Indícios técnicos de manipulação.
- Conteúdo relacionado a uma checagem existente.
- Análise inconclusiva.
- Aguardando revisão humana.

**Importante:** a plataforma não deve utilizar uma simples classificação "verdadeiro" ou "falso" baseada apenas em inteligência artificial.

**[DESENVOLVER — RESPONSÁVEL]**

- Descrever uma situação realista de uso.
- Explicar o que aparece em cada tela.
- Definir como apresentar resultados incertos.
- Indicar como o usuário solicita revisão.

### 2.2 Arquitetura tecnológica

**Arquitetura conceitual sugerida:**

```mermaid
flowchart TD
    A["Usuário"] --> B["Interface web acessível"]
    B --> C["API de análise"]
    C --> D["Validação de proveniência C2PA"]
    C --> E["Análise de áudio e vídeo"]
    C --> F["Busca de checagens semelhantes"]
    D --> G["Motor de evidências"]
    E --> G
    F --> G
    G --> H{"Há evidência suficiente?"}
    H -->|Não| I["Fila de revisão humana"]
    H -->|Sim| J["Relatório com ressalvas"]
    I --> J
    J --> K["Resultado e contestação"]
    C --> L["Armazenamento temporário protegido"]
    G --> M["Registro de auditoria minimizado"]
```

**Componentes propostos:**

| Componente | Função | Tecnologia possível |
|---|---|---|
| Interface | Receber arquivos e exibir análises | React ou HTML/CSS/JS |
| API | Coordenar as solicitações | Python/FastAPI |
| Verificação C2PA | Validar credenciais disponíveis | Ferramentas compatíveis com C2PA |
| Detector | Produzir sinais de manipulação | Modelos de aprendizado de máquina |
| Base de checagens | Consultar verificações anteriores | Banco de dados e busca por similaridade |
| Fila humana | Encaminhar casos complexos | Sistema de gestão de casos |
| Infraestrutura | Executar e monitorar serviços | Ambiente de nuvem |
| Auditoria | Registrar decisões e revisões | Logs protegidos e minimizados |

**Dados de entrada:** arquivo ou link, metadados técnicos disponíveis e informações estritamente necessárias à análise.

**Dados de saída:** relatório, evidências encontradas, limitações e possibilidade de contestação.

**Armazenamento:** inicialmente temporário, com prazo definido conforme finalidade, risco e requisitos legais.

**Acesso:** usuários acessam seus relatórios; revisores autorizados acessam apenas casos atribuídos; administradores possuem permissões limitadas e auditadas.

**[VALIDAR — RESPONSÁVEL]**

- Definir a arquitetura final.
- Justificar as tecnologias escolhidas.
- Explicar criptografia e controle de acesso.
- Definir armazenamento e exclusão.
- Explicar integração entre os componentes.
- Revisar o diagrama Mermaid no GitHub.

### 2.3 Contribuição das áreas profissionais

| Área | Responsabilidade na solução | Entrega técnica esperada |
|---|---|---|
| Ciência de Dados | Avaliar detectores e medir erros | Métricas, testes e análise de vieses |
| Cibersegurança | Garantir integridade e proveniência | Assinaturas, validação C2PA e controles de segurança |
| Engenharia de Dados | Organizar evidências e checagens | Pipeline de dados e mecanismo de busca |
| Cloud Computing | Garantir disponibilidade e escalabilidade | Infraestrutura, monitoramento e controle de custos |
| Gestão de Tecnologia | Organizar revisão e resposta pública | Governança, procedimentos e indicadores |

**[PREENCHER — GRUPO]**

Explicar como as áreas de carreira reais dos integrantes se complementam.

Para cada área representada no grupo, detalhar:

- O problema técnico que resolve.
- O método ou tecnologia utilizada.
- O resultado que entrega.
- A dependência em relação às outras áreas.

### 2.4 Limitações tecnológicas

A proposta apresenta limitações importantes:

- Não existe garantia de detecção perfeita.
- Conteúdos legítimos podem ser classificados incorretamente.
- Conteúdos falsificados podem escapar dos detectores.
- A ausência de credenciais C2PA não significa falsificação.
- Credenciais válidas não comprovam que uma declaração seja verdadeira.
- Modelos podem apresentar desempenho diferente conforme idioma, sotaque ou qualidade do arquivo.
- Revisões humanas podem gerar filas e custos.
- Ataques adversariais podem tentar enganar os mecanismos de análise.

**[DESENVOLVER — RESPONSÁVEL]**

Descrever quais limitações são aceitáveis, quais impediriam a implantação e como a plataforma comunicaria sua incerteza.

---

## 3. Análise ética

**Responsável:** [ Albert dos Santos Mariano ]

### 3.1 Matriz de riscos éticos

| Risco | Categoria | Impacto | Controle proposto |
|---|---|---|---|
| Conteúdo verdadeiro classificado como manipulado | Justiça e reputação | Alto | Revisão humana e contestação |
| Deepfake não identificado | Segurança e informação | Alto | Combinar evidências e comunicar incerteza |
| Desempenho desigual por sotaque | Viés e discriminação | Alto | Testes por grupos e condições de gravação |
| Vazamento de vídeos privados | Privacidade | Alto | Criptografia, acesso restrito e retenção limitada |
| Coleta excessiva de dados | Proteção de dados | Alto | Minimização e descarte |
| Manipulação adversarial do detector | Segurança | Alto | Testes de robustez e monitoramento |
| C2PA interpretado como prova da verdade | Transparência | Alto | Explicação clara do significado da credencial |
| Uso político enviesado da plataforma | Governança | Alto | Critérios públicos, auditoria e revisão independente |

**[DETALHANDO]**

Detalhando probabilidade e gravidade de cada risco, quem pode ser prejudicado, explicar como cada controle seria verificado. 

- **Conteúdo verdadeiro classificado como manipulado:**
  Probabilidade média e gravidade alta de danos reputacionais e censura indevida, Criadores de conteúdo, jorbalistas e utilizadores legítimos serão os mais prejudicados. (Revisão humana e contestação): Verificado por meio de auditorias semanais de solicitações de contestação aprovadas e medição da taxa de falsos positivos


- **Deepfake não identificado:**
  Probabilidade média e alta e gravidade critica de disseminação em larga escala. O público em geral, figuras públicas e alvos diretos de desinformação serão prejudicados. Combinar evidências e comunicar incerteza): Verificado mediante testes de estresse na API de deteção e checagem da interface para assegurar que a incerteza é exibida claramente. 



- **Desempenho desigual por sotaque:**
  Probabilidade alta e gravidade alta de discriminação e exclusão regional. Grupos minoritários e utilizadores de regiões com sotaques menos representados serão mais afetados. (Testes por grupos e condições de gravação): Verificado através da avaliação de métricas de precisão segmentadas por dados demográficos e variações de áudio.  


- **Vazamento de vídeos privados:**
  Probabilidade baixa e média e gravidade muito alta da violação de privacidade e impactos legais. Utilizadores da plataforma e consumidores de notícias, são os públicos mais prejudicados. (Criptografia, acesso restrito e retenção limitada): Verificado por testes de penetração (pentests), auditorias de permissão (IAM) e rotinas automáticas de exclusão de dados. 



- **Coleta excessiva de dados:**
  Probabilidade média e gravidade média e alta de desconformidade com a LGPD. Todos que interagem com o sistemas serão prejudicados. (Minimização e descarte): Verificado mediante revisão do pipeline de engenharia para confirmar que apenas os metadados estritamente necessários são armazenados. (Testes de robustez e monitoramento): Verificado por simulações periódicas de ataques e monitorização contínua de anomalias no tráfego.  


- **Manipulação adversarial do detector:**
  Probabilidade alta de ataques intencionais e gravidade alta de perca de eficácia do sistema. A plataforma e a integridade da informação pública serão afetadas


- **C2PA interpretado como prova da verdade:**
  Probabilidade alta confusão entre proveniência e veracidade factual, e gravidade média e alta. Utilizadores das plataformas e consumidores de notícias não terão segurança 100%.  (Explicação clara do significado da credencial): Verificado por testes de usabilidade e inquéritos de compreensão com utilizadores sobre os selos de procedência.


- **Uso político enviesado da plataforma:**
- Probabilidade média e gravidade crítica, com riscos de interferência política ou eleitoral. A sociedade, partidos políticos e a neutralidade institucional serão afetadas. (Critérios públicos, auditoria e revisão independente): Verificado através da publicação de relatórios transparentes e auditorias externas realizadas por terceiros.



### 3.2 Decisão ética de implantação

**Decisão preliminar: implantar somente com controles.**

A solução não deve ser lançada como ferramenta de julgamento automático da veracidade de conteúdos. Uma implantação piloto dependeria de validação dos modelos, testes de viés, mecanismos de proteção de dados, revisão humana e canal de contestação. Resultados incertos devem ser apresentados como inconclusivos. Casos de maior impacto reputacional ou eleitoral exigem procedimentos reforçados. A continuidade do projeto dependeria das evidências obtidas durante os testes.

**[REVISAR — GRUPO]** Confirmar a decisão e manter a justificativa final em até 10 linhas.

### 3.3 Controles éticos obrigatórios

| Controle | Como funcionaria | Responsável | Evidência verificável |
|---|---|---|---|
| Transparência | Exibir critérios e limitações da análise | [Nome] | Exemplo de relatório |
| Revisão humana | Encaminhar casos críticos ou incertos | [Nome] | Procedimento e registro de revisão |
| Minimização | Coletar apenas dados necessários | [Nome] | Inventário de dados |
| Segurança | Aplicar criptografia e controle de acesso | [Nome] | Checklist de segurança |
| Teste de viés | Comparar taxas de erro entre grupos | [Nome] | Relatório de avaliação |
| Contestação | Permitir revisão de decisões | [Nome] | Fluxo de contestação |
| Auditoria | Registrar alterações e justificativas | [Nome] | Exemplo de trilha de auditoria |

**[DESENVOLVER — RESPONSÁVEL]**

Especificar a frequência de cada controle, os responsáveis e os critérios para verificar sua eficácia.

### 3.4 LGPD e proteção de dados

A Lei Geral de Proteção de Dados deve orientar a coleta, o tratamento, o compartilhamento e a exclusão de informações pessoais.

A base legal de cada operação depende da finalidade e do contexto concreto. Ela não deve ser escolhida automaticamente.

| Dado tratado | Finalidade | Base legal | Prazo de retenção |
|---|---|---|---|
| Arquivo enviado | Realizar análise técnica | [AVALIAR] | [DEFINIR] |
| Metadados do arquivo | Verificar características e proveniência | [AVALIAR] | [DEFINIR] |
| Identificador de solicitação | Permitir acompanhamento | [AVALIAR] | [DEFINIR] |
| Evidências da análise | Justificar o resultado | [AVALIAR] | [DEFINIR] |
| Registro de contestação | Reavaliar decisões | [AVALIAR] | [DEFINIR] |
| Logs de segurança | Proteger a infraestrutura | [AVALIAR] | [DEFINIR] |

**Dados sensíveis e menores de idade:**

Áudios e vídeos podem conter informações pessoais e, dependendo do tratamento, dados biométricos sensíveis. Também podem envolver crianças e adolescentes.

**[PESQUISAR — RESPONSÁVEL]**

- Identificar o controlador e possíveis operadores.
- Justificar cada base legal aplicável.
- Diferenciar dados pessoais comuns e sensíveis.
- Definir critérios de retenção e descarte.
- Descrever procedimentos para conteúdos envolvendo menores.
- Avaliar direitos dos titulares.
- Considerar a necessidade de relatório de impacto à proteção de dados.

Referência: [ANPD — Nota Técnica nº 1/2026](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/documentos-tecnicos-orientativos/nota-tecnica-no-1-2026-fis-cgf-anpd.pdf).

### 3.5 Comunicado público para LinkedIn

**Exemplo provisório — 397 caracteres, incluindo espaços:**

> O VerificaBR é uma proposta acadêmica de verificação assistida de áudios e vídeos suspeitos. O sistema consulta registros de proveniência, compara sinais técnicos e encaminha casos incertos à revisão humana. Nenhuma classificação automática é prova definitiva. Usuários podem entender os motivos da análise e contestar resultados. A ferramenta prioriza privacidade, acessibilidade e transparência.

**[REVISAR — RESPONSÁVEL]**

- Limite máximo: 600 caracteres.
- Conferir a contagem após alterações.
- Manter linguagem acessível ao público.
- Evitar prometer precisão absoluta.

---

## 4. Acessibilidade e inclusão digital

**Responsável:** [Nome do integrante]

### 4.1 Quem poderia ser excluído?

A solução precisa considerar usuários com diferentes condições de acesso à tecnologia.

| Público | Barreira possível | Mitigação proposta |
|---|---|---|
| Pessoas cegas | Interface exclusivamente visual | Compatibilidade com leitores de tela |
| Pessoas com baixa visão | Texto pequeno ou contraste insuficiente | Ajustes visuais e contraste adequado |
| Pessoas surdas | Resultados apresentados apenas em áudio | Transcrições e legendas |
| Pessoas idosas | Navegação complexa | Linguagem simples e fluxo reduzido |
| Pessoas com internet limitada | Arquivos pesados e páginas lentas | Interface leve e informações de consumo |
| Pessoas com baixa alfabetização digital | Termos técnicos incompreensíveis | Explicações e exemplos acessíveis |
| Pessoas com limitações motoras | Dependência do mouse | Navegação completa por teclado |

**[DESENVOLVER — RESPONSÁVEL]**

- Identificar barreiras específicas do público escolhido.
- Explicar alternativas para conexões lentas.
- Definir como o usuário recebe o resultado.
- Propor testes com participantes representativos.

### 4.2 Critérios concretos de acessibilidade

Referência: WCAG 2.2, do W3C.

| Critério WCAG | Aplicação no projeto |
|---|---|
| 1.1.1 — Conteúdo não textual | Alternativas textuais para elementos informativos |
| 1.2.2 — Legendas pré-gravadas | Legendas quando houver vídeo com áudio |
| 1.4.3 — Contraste mínimo | Contraste adequado para textos |
| 2.1.1 — Teclado | Operação sem necessidade de mouse |
| 2.4.7 — Foco visível | Indicação visual do elemento selecionado |
| 2.5.8 — Tamanho do alvo | Controles com área de interação adequada |
| 3.3.1 — Identificação de erros | Mensagens claras sobre erros de formulário |
| 3.3.8 — Autenticação acessível | Evitar barreiras cognitivas desnecessárias |

**[DESENVOLVER — RESPONSÁVEL]**

Explicar como testar os critérios, quais ferramentas seriam utilizadas e como corrigir falhas encontradas.

---

## 5. Sustentabilidade

**Responsável:** João Pedro Theodoro de Sousa Andrade

### 5.1 Sustentabilidade ambiental

O processamento de vídeos e áudios por modelos de inteligência artificial pode exigir recursos computacionais significativos.

**Medidas propostas:**

- Evitar executar modelos pesados quando não forem necessários.
- Verificar proveniência e checagens existentes antes de iniciar análises custosas.
- Aplicar limites de tamanho e duração dos arquivos.
- Excluir dados temporários após o prazo definido.
- Monitorar consumo de processamento e armazenamento.
- Avaliar serviços de nuvem com indicadores ambientais disponíveis.

**[PREENCHER]** Definir métricas ambientais e explicar como seriam acompanhadas.

### 5.2 Sustentabilidade técnica e manutenção

**Medidas propostas:**

- Documentação de componentes e dependências.
- Atualizações periódicas de segurança.
- Monitoramento de desempenho dos modelos.
- Reavaliação dos conjuntos de teste.
- Revisão de incidentes e reclamações.
- Procedimentos para substituição de tecnologias obsoletas.

**[PREENCHER]** Definir responsáveis, frequência e custos de manutenção.

### 5.3 Sustentabilidade financeira após o primeiro ano

**Possibilidades a avaliar:**

- Parcerias com instituições de pesquisa.
- Apoio a projetos de educação midiática.
- Financiamento institucional.
- Convênios com organizações de checagem.
- Serviços especializados, sem comprometer a independência da análise.

| Categoria de custo | Estimativa mensal | Justificativa |
|---|---|---|
| Hospedagem | [R$] | [PREENCHER] |
| Processamento de IA | [R$] | [PREENCHER] |
| Armazenamento | [R$] | [PREENCHER] |
| Segurança | [R$] | [PREENCHER] |
| Revisão humana | [R$] | [PREENCHER] |
| Manutenção | [R$] | [PREENCHER] |

**[DESENVOLVER]** Explicar como o projeto continuaria após 12 meses e quais condições poderiam inviabilizá-lo.

---

## 6. Impacto esperado

**Responsável:** Petterson Michel Lima Aguilar

### 6.1 Indicadores de resultado

As metas abaixo são hipóteses acadêmicas para um piloto. Não representam resultados obtidos.

| Indicador | Como medir | Meta inicial proposta |
|---|---|---|
| Tempo de análise | Mediana do tempo por solicitação | [Definir após teste] |
| Taxa de falsos positivos | Casos legítimos sinalizados incorretamente | [Definir limite aceitável] |
| Taxa de falsos negativos | Deepfakes não identificados | [Definir limite aceitável] |
| Taxa de inconclusivos | Análises sem evidência suficiente | [Definir meta] |
| Satisfação do usuário | Pesquisa após a utilização | [Definir meta] |
| Acessibilidade | Testes WCAG e com usuários | [Definir meta] |
| Contestação | Tempo e resolução das solicitações | [Definir meta] |
| Custo por análise | Gasto total dividido por análises | [Definir meta] |

**[DESENVOLVER — RESPONSÁVEL]**

- Definir metas numéricas realistas.
- Informar a linha de base, quando disponível.
- Explicar como serão coletados os dados.
- Indicar a periodicidade das avaliações.
- Separar resultados técnicos de impactos sociais.

### 6.2 Como ouvir os usuários?

**Métodos propostos:**

- Entrevistas com usuários do público-alvo.
- Testes de usabilidade.
- Questionários de compreensão dos relatórios.
- Canal de feedback e contestação.
- Avaliação com profissionais de checagem.

**[PREENCHER]** Definir participantes, perguntas, critérios de seleção e cuidados com privacidade.

### 6.3 E se a adesão for baixa?

Caso a utilização fique abaixo do esperado, o grupo propõe:

1. Investigar barreiras de acesso.
2. Avaliar a compreensão dos resultados.
3. Reduzir etapas desnecessárias.
4. Melhorar comunicação e acessibilidade.
5. Reavaliar o público-alvo.
6. Verificar se o benefício percebido justifica o esforço de uso.

**[DESENVOLVER]** Definir qual indicador acionaria uma revisão da proposta e quando seria considerada sua descontinuação.

---

## 7. Quadro de decisões

**Responsável:** Petterson Michel Lima Aguilar

| Decisão | Alternativas consideradas | Justificativa preliminar |
|---|---|---|
| Combinar proveniência e detecção | Apenas detector ou apenas C2PA | Reduz dependência de um único mecanismo |
| Incluir resultado inconclusivo | Classificação binária | Evita apresentar certeza indevida |
| Utilizar revisão humana | Automação integral | Permite examinar casos complexos |
| Minimizar armazenamento | Guardar todos os arquivos | Reduz exposição de dados pessoais |
| Priorizar interface web | Aplicativo nativo | Facilita acesso inicial multiplataforma |
| Criar canal de contestação | Resultado sem revisão | Permite corrigir decisões questionáveis |
| Fazer implantação piloto | Lançamento público imediato | Permite avaliar riscos antes de ampliar o uso |

**[DESENVOLVER — GRUPO]**

Para cada decisão:

- Explicar as alternativas reais.
- Apresentar vantagens e desvantagens.
- Indicar evidências que sustentam a escolha.
- Registrar quem participou da decisão.
- Revisar se a decisão continua válida após as pesquisas.

---

## 8. Capítulos individuais

**IMPORTANTE:** cada integrante deve escrever seu próprio capítulo. Os capítulos precisam demonstrar contribuições verificáveis, competências, metas SMART e feedback coletivo.

### 8.1 Capítulo individual — Albert dos Santos Mariano

**Área de carreira:** Engenharia de Dados 
**GitHub:** AlbertdosSantosMariano

#### 8.1.1 Papel no projeto e entregas verificáveis

**Responsabilidades assumidas:**

[Descrever o que fez e por que sua área profissional foi importante.]

**Entregas realizadas:**

- [Entrega 1]
- [Entrega 2]
- [Entrega 3]

**Evidências no GitHub:**

- Commit: [Link]
- Pull request: [Link]

#### 8.1.2 Competências técnicas e comportamentais

| Tipo | Competências que já possuo | Competências que preciso desenvolver |
|---|---|---|
| Técnicas | [PREENCHER] | [PREENCHER] |
| Comportamentais | [PREENCHER] | [PREENCHER] |

#### 8.1.3 Plano de desenvolvimento — metas SMART

**Meta 1 (6 meses):** [Objetivo específico, mensurável, alcançável, relevante e com prazo.]

**Meta 2 (12 meses):** [Objetivo específico, mensurável, alcançável, relevante e com prazo.]

**Como comprovarei os resultados:** [Cursos, projetos, certificações, portfólio ou entregas.]

#### 8.1.4 Feedback coletivo

**Pontos fortes identificados pelos colegas:**

[PREENCHER com feedback real.]

**Pontos de melhoria:**

[PREENCHER com feedback real.]

**Como utilizarei esse feedback:**

[PREENCHER.]

---

### 8.2 Capítulo individual — Gabriel Anjos Albuquerque

**Área de carreira:** Engenharia de Dados  
**GitHub:** Nerd8im
#### 8.2.1 Papel no projeto e entregas verificáveis

**Responsabilidades:** [PREENCHER]

**Entregas realizadas:**

- [Entrega 1]
- [Entrega 2]
- [Entrega 3]

**Commits e pull requests:** [Links]

#### 8.2.2 Competências técnicas e comportamentais

| Tipo | Já possuo | Preciso desenvolver |
|---|---|---|
| Técnicas | [PREENCHER] | [PREENCHER] |
| Comportamentais | [PREENCHER] | [PREENCHER] |

#### 8.2.3 Plano de desenvolvimento — metas SMART

**Meta de 6 meses:** [PREENCHER]

**Meta de 12 meses:** [PREENCHER]

**Indicadores, ações e evidências:** [PREENCHER]

#### 8.2.4 Feedback coletivo

**Pontos fortes:** [Feedback dos colegas]

**Pontos de melhoria:** [Feedback dos colegas]

**Ações a partir do feedback:** [PREENCHER]

---

### 8.3 Capítulo individual — João Pedro Theodoro de Sousa Andrade

**Área de carreira:** Ciência de Dadoss
**GitHub:** jp-theodoro

#### 8.3.1 Papel no projeto e entregas verificáveis

**Responsabilidades:** Formatar e organizar o arquivo, deixando organizado, facilitando a compreensão das informações. Além disso, responsável pela parte 5 (Sustentabilidade).

**Commits e pull requests:**

1º commit: Adicionar esqueleto do documento, organizando para os outros integrantes adicionarem suas partes e separar a função de cada integrante.

#### 8.3.2 Competências técnicas e comportamentais

**Competência que a solução exige:** Organização, liderança, proatividade, senso de sociedade, empatia, pensamento crítico, gestão de projetos, TI verde, entre outras competências similares.
**Já possuo:**  Organização, liderança, senso de sociedade, empatia, TI verde. 

Claro, que preciso desenvolver as outras competências para melhor desempenho!

#### 8.3.3 Plano de desenvolvimento — metas SMART

**Meta de 6 meses:** Pretendo aprofundar meus conhecimentos sobre sustentabilidade na área de Tecnologia da Informação, por meio de estudos e da realização de pelo menos um curso sobre TI Verde. Como resultado, pretendo elaborar um relatório identificando três estratégias para reduzir o consumo de energia, o armazenamento desnecessário e os custos operacionais da plataforma de verificação de deepfakes.

**Meta de 12 meses:** Quero desenvolver minhas competências em gestão de recursos tecnológicos e planejamento financeiro, estudando conceitos básicos de Cloud Computing e análise de custos. Meu objetivo será elaborar um planejamento de sustentabilidade para a plataforma, contendo uma estimativa de custos operacionais, pelo menos três medidas de otimização de recursos e duas possibilidades de financiamento ou parceria para garantir a continuidade do projeto.

#### 8.3.4 Feedback coletivo

**Pontos fortes:** [Feedback dos colegas]

**Pontos de melhoria:** [Feedback dos colegas]

**Ações a partir do feedback:** [PREENCHER]

---

### 8.4 Capítulo individual — Petterson Michel Lima Aguilar

**Área de carreira:** Engenharia de Dados
**GitHub:** PettersonAguilar

#### 8.4.1 Papel no projeto e entregas verificáveis

**Responsabilidades:** [PREENCHER]

**Entregas realizadas:**

- [Entrega 1]
- [Entrega 2]
- [Entrega 3]

**Commits e pull requests:** [Links]

#### 8.4.2 Competências técnicas e comportamentais

| Tipo | Já possuo | Preciso desenvolver |
|---|---|---|
| Técnicas | [PREENCHER] | [PREENCHER] |
| Comportamentais | [PREENCHER] | [PREENCHER] |

#### 8.4.3 Plano de desenvolvimento — metas SMART

**Meta de 6 meses:** [PREENCHER]

**Meta de 12 meses:** [PREENCHER]

**Indicadores, ações e evidências:** [PREENCHER]

#### 8.4.4 Feedback coletivo

**Pontos fortes:** [Feedback dos colegas]

**Pontos de melhoria:** [Feedback dos colegas]

**Ações a partir do feedback:** [PREENCHER]

---

### 8.5 Capítulo individual — Samuel Carmoni de Oliveira

**Área de carreira:** Cybersegurança
**GitHub:** Samuel Carmoni

#### 8.5.1 Papel no projeto e entregas verificáveis

**Responsabilidades:** [PREENCHER]

**Entregas realizadas:**

- [Entrega 1]
- [Entrega 2]
- [Entrega 3]

**Commits e pull requests:** [Links]

#### 8.5.2 Competências técnicas e comportamentais

| Tipo | Já possuo | Preciso desenvolver |
|---|---|---|
| Técnicas | [PREENCHER] | [PREENCHER] |
| Comportamentais | [PREENCHER] | [PREENCHER] |

#### 8.5.3 Plano de desenvolvimento — metas SMART

**Meta de 6 meses:** [PREENCHER]

**Meta de 12 meses:** [PREENCHER]

**Indicadores, ações e evidências:** [PREENCHER]

#### 8.5.4 Feedback coletivo

**Pontos fortes:** [Feedback dos colegas]

**Pontos de melhoria:** [Feedback dos colegas]

**Ações a partir do feedback:** [PREENCHER]

---

## 9. Referências

As referências abaixo são sugestões iniciais de fontes para o Dossiê 4. O grupo deve conferir os dados, as datas e a correspondência entre as citações do texto e a lista final.

### Legislação e documentos oficiais

1. BRASIL. **Lei nº 13.709/2018 — Lei Geral de Proteção de Dados Pessoais (LGPD)**. Versão vigente. Disponível em: https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm

2. TRIBUNAL SUPERIOR ELEITORAL. **Resolução nº 23.610/2019**. Texto compilado vigente. Disponível em: https://www.tse.jus.br/legislacao/compilada/res/2019/resolucao-no-23-610-de-18-de-dezembro-de-2019?texto=compilado

3. TRIBUNAL SUPERIOR ELEITORAL. **Resolução nº 23.755, de 2 de março de 2026**. Disponível em: https://www.tse.jus.br/legislacao/compilada/res/2026/resolucao-no-23-755-de-2-de-marco-de-2026

4. AUTORIDADE NACIONAL DE PROTEÇÃO DE DADOS. **Nota Técnica nº 1/2026**. Disponível em: https://www.gov.br/anpd/pt-br/centrais-de-conteudo/documentos-tecnicos-orientativos/nota-tecnica-no-1-2026-fis-cgf-anpd.pdf

### Normas e especificações técnicas

5. COALITION FOR CONTENT PROVENANCE AND AUTHENTICITY. **C2PA Technical Specification, versão 2.2**. Disponível em: https://spec.c2pa.org/specifications/specifications/2.2/index.html

6. WORLD WIDE WEB CONSORTIUM. **Web Content Accessibility Guidelines (WCAG) 2.2**. Recomendação vigente. Disponível em: https://www.w3.org/TR/WCAG22/

### Pesquisas acadêmicas

7. **Deepfake-Eval-2024: A Multi-Modal In-the-Wild Benchmark of Deepfakes Circulated in 2024**. 2025. Disponível em: https://doi.org/10.48550/arXiv.2503.02857

8. **BRSpeech-DF: A Deep Fake Synthetic Speech Dataset for Portuguese Zero-Shot TTS**. 2025. Disponível em: https://aclanthology.org/2025.emnlp-main.1780.pdf

### Pesquisas e checagem de fatos no Brasil

9. DATA PRIVACY BRASIL. **IA na pré-eleição: deepfakes, desinformação e novos desafios para a integridade das eleições de 2026**. Disponível em: https://www.dataprivacybr.org/documentos/ia-na-pre-eleicao-deepfakes-desinformacao-e-novos-desafios-para-a-integridade-das-eleicoes-de-2026/

10. AGÊNCIA LUPA. **Projeto VigIA**. 2026. Disponível em: https://www.agencialupa.org/observatorio-lupa/projeto-vigia/

11. AGÊNCIA BRASIL. **Mesmo proibidos, deepfakes tomam conta das redes antes da eleição**. Outubro de 2026. Disponível em: https://agenciabrasil.ebc.com.br/geral/noticia/2026-10/mesmo-proibidos-deepfakes-tomam-conta-das-redes-antes-da-eleicao

12. AOS FATOS. **Da IA ultrarrealista ao WhatsApp, como a desinformação moldou as eleições**. Outubro de 2026. Disponível em: https://www.aosfatos.org/noticias/ia-ultrarrealista-whatsapp-desinformacao-moldou-eleicoes/

**[PREENCHER — GRUPO]**

- Acrescentar as referências utilizadas pelos integrantes.
- Conferir autoria, título, ano, URL e data de acesso.
- Priorizar publicações a partir de novembro de 2024.
- Utilizar leis e normas pela versão vigente.
- Remover referências que não tenham sido utilizadas.
- Garantir que toda afirmação quantitativa esteja acompanhada de fonte.

---

<!--
=====================================================
CHECKLIST FINAL DE ENTREGA
=====================================================

[ ok ] Grupo com 3 a 5 integrantes.
[ ok ] Integrantes em ordem alfabética.
[ok  ] Nome, RGM, GitHub e área de carreira preenchidos.
[ ok ] Dossiê e recorte justificados.
[ ] Problema com dados e fontes.
[ ] Causas técnicas aprofundadas.
[ ] Soluções existentes comparadas.
[ ] Fluxo de usuário detalhado.
[ ] Arquitetura e diagrama revisados.
[ ] Contribuição de cada área profissional explicada.
[ ] Limitações tecnológicas apresentadas.
[ ] Matriz com pelo menos 5 riscos.
[ ] Decisão ética justificada em até 10 linhas.
[ ] Pelo menos 6 controles éticos com responsável e evidência.
[ ] Tabela LGPD preenchida e validada.
[ ] Comunicado público com até 600 caracteres.
[ ] Acessibilidade com critérios WCAG concretos.
[ ] Inclusão digital discutida.
[ ] Sustentabilidade ambiental, técnica e financeira.
[ ] Métricas com metas mensuráveis.
[ ] Métodos para ouvir usuários.
[ ] Plano para baixa adesão.
[ ] Pelo menos 5 decisões justificadas.
[ ] Capítulo individual de cada integrante.
[ ] Competências técnicas e comportamentais.
[ ] Metas SMART para 6 a 12 meses.
[ ] Feedback coletivo em cada capítulo.
[ ] Referências recentes e links conferidos.
[ ] Apenas um arquivo .md para a entrega.
[ ] Repositório público novo no GitHub.
[ ] Todos os integrantes com commits próprios.
[ ] Pull requests e contribuições verificáveis.
[ ] Revisão de ortografia, coerência e formatação.
[ ] Preparação de todos para a arguição.
[ ] Entrega até 09/11/2026 às 23h59.

=====================================================
-->
