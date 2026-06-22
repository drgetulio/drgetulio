# PRD — Aplicativo de Cadastro de Pacientes Cardiopatas
## Instituto Corações em Rede

> **Documento de Requisitos de Produto (Product Requirements Document)**
> Aplicativo para cadastro, acompanhamento e busca de pacientes cardiopatas com necessidades específicas de doação (medicamentos, produtos dietéticos e exames de alto custo).

---

## Controle do Documento

| Campo | Valor |
|---|---|
| **Produto** | Aplicativo de Cadastro de Pacientes Cardiopatas |
| **Organização** | Instituto Corações em Rede — https://coracoesemrede.org/ |
| **Versão** | 1.0 |
| **Data** | 22/06/2026 |
| **Status** | Proposta para aprovação |
| **Classificação** | Confidencial — contém referências a tratamento de dados pessoais sensíveis |
| **Responsável pelo produto** | Time de Produto |
| **Aprovadores** | Direção do Instituto · Encarregado de Dados (DPO) · Coordenação Clínica |

### Histórico de Revisões

| Versão | Data | Descrição | Autor |
|---|---|---|---|
| 1.0 | 22/06/2026 | Versão inicial do PRD | Time de Produto |

---

## Sumário

1. [Resumo Executivo](#1-resumo-executivo)
2. [Contexto e Justificativa](#2-contexto-e-justificativa)
3. [Objetivos e Métricas de Sucesso](#3-objetivos-e-métricas-de-sucesso)
4. [Escopo, Premissas e Restrições](#4-escopo-premissas-e-restrições)
5. [Personas e Perfis de Usuário](#5-personas-e-perfis-de-usuário)
6. [Matriz de Permissões (RBAC)](#6-matriz-de-permissões-rbac)
7. [Requisitos Funcionais](#7-requisitos-funcionais)
8. [Requisitos Não Funcionais](#8-requisitos-não-funcionais)
9. [Conformidade com a LGPD](#9-conformidade-com-a-lgpd)
10. [Modelo de Dados](#10-modelo-de-dados)
11. [Fluxos Principais](#11-fluxos-principais)
12. [Arquitetura e Stack Tecnológica](#12-arquitetura-e-stack-tecnológica)
13. [Identidade Visual e Design System](#13-identidade-visual-e-design-system)
14. [Acessibilidade](#14-acessibilidade)
15. [Roadmap e Fases de Entrega](#15-roadmap-e-fases-de-entrega)
16. [Riscos e Mitigações](#16-riscos-e-mitigações)
17. [Definição de Pronto (Definition of Done)](#17-definição-de-pronto-definition-of-done)
18. [Questões em Aberto](#18-questões-em-aberto)
19. [Glossário](#19-glossário)
20. [Anexos](#20-anexos)

---

## 1. Resumo Executivo

O **Instituto Corações em Rede** é uma organização da sociedade civil que apoia **pacientes cardiopatas** em situação de vulnerabilidade, conectando suas necessidades de saúde a uma rede de doadores e parceiros.

Hoje, o acompanhamento dessas necessidades depende de planilhas, mensagens e registros dispersos, o que dificulta encontrar rapidamente *quem precisa de quê*, comprometendo a agilidade do atendimento e a segurança dos dados.

Este documento especifica um **aplicativo web responsivo** que permite a profissionais autorizados:

- **Cadastrar e acompanhar pacientes cardiopatas** e seus diagnósticos;
- **Registrar necessidades específicas** em três categorias — **medicamentos**, **produtos dietéticos** e **exames de alto custo** (ecocardiograma, angiotomografia, ressonância e cateterismo);
- **Buscar pacientes por necessidade específica**, com filtros combináveis e ordenação por urgência;
- Operar sob **governança de acesso**, na qual um **administrador** habilita os demais profissionais;
- Cumprir integralmente a **Lei Geral de Proteção de Dados (LGPD — Lei nº 13.709/2018)**, tratando dados de saúde como **dados pessoais sensíveis**.

O produto adota a **identidade visual do Instituto** (paleta derivada da logomarca) e linguagem acolhedora, digna e clara, condizente com o público atendido.

---

## 2. Contexto e Justificativa

### 2.1 Problema

Pacientes cardiopatas frequentemente dependem de itens e serviços de **alto custo e indisponibilidade no sistema público** — medicamentos contínuos, dietas específicas e exames diagnósticos caros. As necessidades são **urgentes, recorrentes e heterogêneas**, e a captação de doações exige saber, em tempo real, **qual paciente precisa de qual recurso**.

### 2.2 Situação atual (dores)

- Registros em **planilhas e mensagens**, sem padronização nem trilha de auditoria.
- **Dificuldade de busca**: localizar "todos os pacientes que precisam de ecocardiograma" exige varredura manual.
- **Risco à privacidade**: dados sensíveis de saúde circulam sem controle de acesso nem base legal documentada.
- **Falta de visibilidade gerencial**: não há indicadores de necessidades abertas, atendidas e prazos.
- **Dependência de pessoas-chave**: o conhecimento fica concentrado em poucos voluntários.

### 2.3 Oportunidade

Uma ferramenta única, segura e simples que **centraliza o cadastro**, **estrutura as necessidades** e **viabiliza a busca por necessidade específica** reduz o tempo entre identificar a carência e mobilizar a doação, ampliando o impacto social do Instituto com **conformidade legal** e **dignidade no tratamento dos dados**.

---

## 3. Objetivos e Métricas de Sucesso

### 3.1 Objetivos de produto

| # | Objetivo |
|---|---|
| O1 | Centralizar o cadastro de pacientes cardiopatas em uma base única, segura e auditável. |
| O2 | Estruturar as necessidades específicas em categorias padronizadas e pesquisáveis. |
| O3 | Permitir a busca por necessidade específica em segundos, com filtros combináveis. |
| O4 | Garantir governança de acesso, com administrador habilitando profissionais. |
| O5 | Assegurar conformidade plena com a LGPD para dados de saúde. |

### 3.2 Métricas de sucesso (KPIs)

| KPI | Definição | Meta inicial |
|---|---|---|
| Tempo de busca por necessidade | Tempo médio para localizar pacientes por um critério | < 5 segundos |
| Necessidades atendidas | % de necessidades abertas que evoluem para "atendida" | ≥ 70% em 6 meses |
| Necessidades críticas no prazo | % de necessidades "críticas" atendidas dentro do prazo definido | ≥ 90% |
| Adoção | Profissionais ativos / profissionais cadastrados (mensal) | ≥ 80% |
| Qualidade do cadastro | % de cadastros com campos obrigatórios e consentimento completos | ≥ 95% |
| Incidentes de privacidade | Número de incidentes de segurança/privacidade reportados | 0 |

> As metas devem ser revisadas com a Direção após o primeiro trimestre de operação.

---

## 4. Escopo, Premissas e Restrições

### 4.1 Dentro do escopo (MVP)

- Autenticação e controle de acesso baseado em papéis (RBAC).
- Gestão de usuários pelo administrador (convite, ativação, suspensão).
- Cadastro de pacientes (CRUD) com diagnóstico de cardiopatia.
- Registro de necessidades específicas (medicamentos, produtos dietéticos, exames de alto custo).
- **Busca e filtros por necessidade específica.**
- Gestão de consentimento e registro de base legal (LGPD).
- Trilha de auditoria de acessos e alterações.
- Anexos de documentos de apoio (receitas, laudos, pedidos médicos).

### 4.2 Fora do escopo (MVP)

- Portal público de autocadastro pelo próprio paciente.
- Portal externo para doadores (previsto para fase posterior).
- Integração automática com sistemas hospitalares, laboratórios ou o SUS.
- Emissão de prontuário eletrônico clínico completo (o produto **não substitui** prontuário médico).
- Aplicativo nativo para lojas (a entrega inicial é web responsivo, instalável como PWA).
- Funcionalidades de pagamento ou arrecadação financeira on-line.

### 4.3 Premissas

- O público são pacientes cardiopatas (adultos e menores), exigindo suporte a **representante legal** para menores e incapazes.
- Os profissionais possuem dispositivos com navegador moderno e acesso à internet.
- O Instituto atuará como **Controlador** dos dados e designará um **Encarregado (DPO)**.
- A hospedagem ocorrerá em **infraestrutura situada no Brasil**, evitando transferência internacional de dados.
- O idioma do produto é **português do Brasil (pt-BR)**.

### 4.4 Restrições

- Conformidade obrigatória com a **LGPD** e demais normas aplicáveis a dados de saúde.
- Orçamento e equipe de uma organização do terceiro setor — priorizar simplicidade e baixo custo operacional.
- O produto não realiza diagnóstico nem prescrição; é uma ferramenta **administrativa e assistencial de apoio**.

---

## 5. Personas e Perfis de Usuário

### 5.1 Administrador (Gestor do Instituto)
Coordena o uso da ferramenta. **Habilita e gerencia os profissionais**, define catálogos (ex.: tipos de necessidade), acompanha indicadores e zela pela governança e conformidade. É o perfil de maior privilégio.

### 5.2 Profissional de Saúde / Assistência
Médico, enfermeiro, nutricionista ou assistente social vinculado ao Instituto. **Cadastra e atualiza pacientes e necessidades**, registra consentimento, anexa documentos e realiza buscas. Só atua após habilitação pelo administrador.

### 5.3 Coordenador (opcional)
Perfil intermediário com visão ampliada de relatórios e supervisão das equipes, **sem** poderes de administração de usuários. Pode ser ativado conforme a estrutura do Instituto.

### 5.4 Paciente (titular dos dados)
**Não é usuário do sistema no MVP**, mas é o **titular dos dados pessoais sensíveis**. Tem direitos garantidos pela LGPD (acesso, correção, revogação de consentimento etc.), exercidos por meio do Instituto.

---

## 6. Matriz de Permissões (RBAC)

Princípio do **menor privilégio**: cada perfil acessa apenas o necessário.

| Recurso / Ação | Administrador | Coordenador | Profissional |
|---|:---:|:---:|:---:|
| Gerenciar usuários (convidar, ativar, suspender) | ✅ | ❌ | ❌ |
| Definir papéis e permissões | ✅ | ❌ | ❌ |
| Cadastrar / editar pacientes | ✅ | ✅ | ✅ |
| Visualizar pacientes | ✅ | ✅ | ✅ |
| Excluir / anonimizar paciente | ✅ | ❌ | ❌ |
| Registrar / editar necessidades | ✅ | ✅ | ✅ |
| Buscar por necessidade específica | ✅ | ✅ | ✅ |
| Registrar atendimento de necessidade / doação | ✅ | ✅ | ✅ |
| Gerenciar catálogos (tipos de necessidade) | ✅ | ❌ | ❌ |
| Exportar dados | ✅ | ✅ (restrito) | ❌ |
| Visualizar relatórios e indicadores | ✅ | ✅ | ✅ (limitado) |
| Acessar trilha de auditoria | ✅ | ❌ | ❌ |
| Configurar parâmetros e consentimento | ✅ | ❌ | ❌ |

> Toda ação sobre dados sensíveis é **registrada em trilha de auditoria**, independentemente do perfil.

---

## 7. Requisitos Funcionais

> Formato: cada requisito traz **histórias de usuário**, **critérios de aceite** e **prioridade** (MoSCoW — *Must / Should / Could*).

### RF-01 — Autenticação e Controle de Acesso · *Must*

**História:** Como usuário autorizado, quero acessar o sistema com credenciais seguras, para proteger os dados dos pacientes.

**Critérios de aceite:**
- Login por e-mail e senha, com **senha forte** (mínimo 10 caracteres, combinação de tipos) e armazenamento via *hash* com algoritmo robusto (ex.: Argon2/bcrypt).
- **Autenticação multifator (MFA)** obrigatória para o perfil Administrador e configurável para os demais.
- **Bloqueio temporário** após tentativas sucessivas malsucedidas.
- **Encerramento de sessão por inatividade** (ex.: 15 minutos) e logout manual.
- Fluxo de **redefinição de senha** por link temporário enviado ao e-mail cadastrado.
- Nenhuma área protegida acessível sem sessão válida.

### RF-02 — Gestão de Usuários pelo Administrador · *Must*

**História:** Como administrador, quero habilitar e gerenciar os profissionais, para que apenas pessoas autorizadas cadastrem pacientes.

**Critérios de aceite:**
- O administrador **convida** um profissional informando nome, e-mail e perfil; o convite gera acesso pendente.
- O profissional conclui o cadastro definindo a própria senha por link seguro e expira em prazo definido.
- O administrador pode **ativar, suspender e reativar** contas, e **alterar o perfil** de um usuário.
- Ao suspender uma conta, as sessões ativas do usuário são encerradas.
- Registro do conselho profissional e número (ex.: CRM, COREN, CRN, CRESS) quando aplicável.
- Toda criação/alteração de usuário é registrada na auditoria com autor e data.

### RF-03 — Cadastro de Pacientes (CRUD) · *Must*

**História:** Como profissional, quero cadastrar e manter os dados do paciente, para acompanhar suas necessidades.

**Critérios de aceite:**
- Formulário com **dados de identificação** (nome completo, nome social, data de nascimento, sexo/gênero, documentos), **contato** e **endereço**.
- Suporte a **representante legal** (nome, parentesco, contato) para menores e incapazes, conforme Art. 14 da LGPD.
- Campos obrigatórios validados; CPF validado quanto ao formato e dígito verificador.
- **Coleta de consentimento** vinculada ao cadastro (ver RF-07) antes da finalização.
- Edição com versionamento e registro de quem alterou o quê (auditoria).
- **Inativação lógica** (status: ativo, inativo, alta, óbito) em vez de exclusão física, preservando histórico, salvo solicitação de eliminação (LGPD).
- Listagem paginada com **mascaramento** de dados sensíveis (ex.: CPF parcial).

### RF-04 — Diagnóstico de Cardiopatia · *Must*

**História:** Como profissional, quero registrar a cardiopatia do paciente, para contextualizar suas necessidades.

**Critérios de aceite:**
- Registro da(s) **cardiopatia(s)** com descrição e, opcionalmente, **código CID-10**.
- Campo opcional de **classe funcional (NYHA I–IV)** e data do diagnóstico.
- Possibilidade de anexar laudos/documentos de apoio (ver RF-09).

### RF-05 — Registro de Necessidades Específicas · *Must*

**História:** Como profissional, quero registrar as necessidades específicas do paciente, para que possam ser localizadas e atendidas.

**Categorias e campos:**

| Categoria | Campos específicos |
|---|---|
| **Medicamento** | Nome/princípio ativo, dosagem, posologia, quantidade, uso contínuo (sim/não) |
| **Produto Dietético** | Tipo/descrição, quantidade, periodicidade |
| **Exame de Alto Custo** | Tipo do exame: **Ecocardiograma**, **Angiotomografia**, **Ressonância**, **Cateterismo** (catálogo extensível) |

**Critérios de aceite (todas as categorias):**
- Cada necessidade possui **prioridade/urgência**: *Crítica · Alta · Média · Baixa*.
- **Status** do ciclo de vida: *Aberta · Em andamento · Atendida · Cancelada · Expirada*.
- **Prazo desejado / validade** da necessidade e **justificativa clínica**.
- **Recorrência**: única, mensal ou contínua.
- Vínculo ao **profissional solicitante**, data de solicitação e quantidade/unidade.
- Possibilidade de anexar documento de suporte (receita, pedido médico, laudo).
- O catálogo de tipos de exame e demais listas é **gerenciável pelo administrador** (extensível sem nova versão do sistema).

### RF-06 — Busca e Filtros por Necessidade Específica · *Must* (diferencial central)

**História:** Como profissional, quero buscar pacientes por necessidade específica, para mobilizar doações com rapidez.

**Critérios de aceite:**
- **Filtros combináveis**, incluindo:
  - Categoria (medicamento · produto dietético · exame de alto custo);
  - **Tipo de exame** (ecocardiograma, angiotomografia, ressonância, cateterismo);
  - Nome do medicamento / produto dietético (busca textual);
  - Prioridade/urgência;
  - Status da necessidade;
  - Localização (cidade/UF);
  - Faixa etária e profissional responsável.
- **Ordenação** por urgência, prazo ou data de solicitação.
- Resultado em lista com **mascaramento** de dados sensíveis e contagem total.
- **Filtros salvos** para consultas recorrentes (ex.: "Aguardando ecocardiograma").
- **Exportação** do resultado restrita a perfis autorizados, **registrada na auditoria** e com aviso de responsabilidade sobre dados sensíveis.
- Desempenho: retorno do resultado em **menos de 3 segundos** para a base esperada.

> Exemplo de uso: *"Listar todos os pacientes com necessidade aberta de **ressonância**, prioridade **Crítica**, na cidade de **Volta Redonda**, ordenados por **prazo**."*

### RF-07 — Consentimento e Base Legal (LGPD) · *Must*

**História:** Como Instituto (Controlador), quero registrar a base legal e o consentimento, para tratar dados de saúde em conformidade com a LGPD.

**Critérios de aceite:**
- Registro da **base legal** do tratamento (ver Seção 9), com **termo de consentimento versionado** quando aplicável.
- Captura de **finalidades** consentidas, data, forma de coleta e evidência (documento assinado/aceite).
- **Revogação de consentimento** registrável, com data e efeito sobre o tratamento.
- Bloqueio de finalidades acessórias (ex.: divulgação em campanha) quando não houver consentimento específico.
- Tratamento de dados de **crianças e adolescentes** condicionado ao consentimento do responsável e ao seu **melhor interesse** (Art. 14).

### RF-08 — Atendimento de Necessidades / Doações · *Should*

**História:** Como profissional, quero registrar o atendimento de uma necessidade, para acompanhar o que já foi suprido.

**Critérios de aceite:**
- Vínculo entre **necessidade** e **doação/atendimento** (item, serviço, agendamento de exame).
- Registro de quantidade/valor, data, doador (identificado ou anônimo) e status (*prometida · recebida · entregue ao paciente*).
- Possibilidade de anexar comprovante.
- Ao atender integralmente, a necessidade muda para **Atendida** automaticamente (ou parcialmente, mantendo o saldo).

### RF-09 — Anexos e Documentos · *Should*

**História:** Como profissional, quero anexar documentos de apoio, para comprovar e justificar as necessidades.

**Critérios de aceite:**
- Upload de arquivos (PDF e imagens) vinculados a paciente, necessidade ou doação.
- Armazenamento **criptografado**, com acesso por **URLs assinadas e temporárias**.
- Registro de tipo (laudo, receita, comprovante, termo), autor, data e *hash* de integridade.
- Limite de tamanho e validação de tipo de arquivo; verificação contra arquivos maliciosos.

### RF-10 — Relatórios e Indicadores · *Should*

**História:** Como gestor, quero visualizar indicadores, para tomar decisões e prestar contas.

**Critérios de aceite:**
- Painel com **necessidades abertas × atendidas**, por categoria e prioridade.
- Indicadores de **tempo médio de atendimento** e **necessidades críticas no prazo**.
- Relatórios **agregados/anonimizados** para uso estatístico e prestação de contas.
- Exportação de relatórios em formato aberto (ex.: CSV), respeitando perfis e auditoria.

### RF-11 — Notificações · *Could*

**História:** Como profissional, quero ser avisado sobre necessidades urgentes e prazos, para agir a tempo.

**Critérios de aceite:**
- Avisos in-app (e, opcionalmente, por e-mail) sobre **necessidades críticas** e **prazos próximos do vencimento**.
- Preferências de notificação configuráveis por usuário.

### RF-12 — Trilha de Auditoria · *Must*

**História:** Como administrador/DPO, quero registrar quem acessou e alterou cada dado, para garantir rastreabilidade e conformidade.

**Critérios de aceite:**
- Registro **imutável** de eventos: autenticação, leitura, criação, edição, exclusão, exportação e busca de dados sensíveis.
- Cada evento contém **quem, o quê, quando, de onde** (usuário, entidade, ação, data/hora, IP/dispositivo).
- Consulta filtrável da auditoria pelo administrador/DPO.
- Os registros de auditoria **não armazenam** o conteúdo sensível em texto claro além do necessário para rastreabilidade.

### RF-13 — Direitos do Titular (LGPD) · *Must*

**História:** Como Instituto, quero atender às solicitações do titular, para cumprir os direitos garantidos pela LGPD.

**Critérios de aceite:**
- Funções para **confirmar tratamento, acessar, corrigir, portar, anonimizar/eliminar** dados de um titular e **registrar a revogação** de consentimento.
- Toda solicitação atendida fica registrada com data e responsável.
- A eliminação respeita obrigações legais de guarda; quando aplicável, realiza-se **anonimização** em vez de exclusão.

---

## 8. Requisitos Não Funcionais

### 8.1 Segurança
- **Criptografia em trânsito** (TLS 1.2+) e **em repouso** (AES-256).
- **Criptografia/pseudonimização em nível de campo** para identificadores sensíveis (ex.: CPF).
- RBAC com **menor privilégio**, MFA para administradores e gestão segura de segredos.
- Proteção contra ameaças comuns (injeção, XSS, CSRF, quebra de controle de acesso) seguindo boas práticas reconhecidas (ex.: OWASP).
- Política de senha forte, bloqueio por tentativas e expiração de sessão.

### 8.2 Privacidade desde a concepção (*Privacy by Design & by Default*)
- Minimização de dados: coletar apenas o necessário às finalidades declaradas.
- Mascaramento de dados sensíveis em listas e telas por padrão.
- Configurações padrão sempre as mais protetivas.

### 8.3 Desempenho
- Buscas por necessidade retornam em **< 3 s** para a base esperada.
- Operações de cadastro/edição respondem em **< 1 s** em condições normais.

### 8.4 Disponibilidade e Continuidade
- Meta de disponibilidade **≥ 99,5%** mensal.
- **Backups diários criptografados**, com **RPO ≤ 24 h** e **RTO ≤ 8 h**.
- Plano de recuperação de desastres documentado e testado periodicamente.

### 8.5 Escalabilidade e Manutenibilidade
- Arquitetura capaz de crescer com o número de pacientes e profissionais sem reescrita.
- Código modular, documentado e coberto por testes automatizados.

### 8.6 Usabilidade
- Interface simples, em português, utilizável por profissionais não técnicos.
- Fluxos principais concluídos em poucos passos; mensagens de erro claras e orientativas.
- Responsivo para uso em computador, tablet e celular.

### 8.7 Compatibilidade
- Navegadores modernos (versões atuais de Chrome, Firefox, Edge e Safari).
- Instalável como **PWA**, com tela de toque e bom desempenho em conexões móveis.

### 8.8 Observabilidade
- Registro de logs técnicos e de aplicação (sem dados sensíveis em texto claro).
- Monitoramento de disponibilidade, erros e desempenho com alertas.

### 8.9 Localização
- Datas, números e formatos em **pt-BR**; fuso horário de Brasília.

---

## 9. Conformidade com a LGPD

> Dados de **saúde** são **dados pessoais sensíveis** (LGPD, Art. 5º, II), exigindo proteção reforçada (Art. 11). Esta seção orienta o desenho do produto; a definição final das bases legais deve ser validada pelo **Encarregado (DPO)** e pela assessoria jurídica do Instituto.

### 9.1 Papéis
- **Controlador:** Instituto Corações em Rede — define finalidades e meios do tratamento.
- **Operador:** eventual fornecedor de tecnologia/hospedagem — trata dados em nome do Controlador, regido por **contrato com cláusulas de proteção de dados**.
- **Encarregado (DPO):** pessoa indicada como canal entre titulares, Instituto e ANPD (Art. 41), com contato divulgado no aplicativo.

### 9.2 Bases legais sugeridas (a confirmar com o DPO)
- **Tutela da saúde**, em procedimento realizado por profissionais de saúde ou serviços de saúde (Art. 11, II, "f") — base principal para o tratamento assistencial.
- **Proteção da vida ou da incolumidade física** do titular (Art. 11, II, "e"), quando aplicável.
- **Consentimento específico e destacado** (Art. 11, I) para **finalidades acessórias** — por exemplo, exposição de caso em campanha de captação ou compartilhamento de dados identificáveis com doadores/parceiros.

### 9.3 Princípios observados (Art. 6º)
Finalidade · adequação · **necessidade (minimização)** · livre acesso · qualidade dos dados · transparência · **segurança** · prevenção · não discriminação · responsabilização e prestação de contas.

### 9.4 Direitos do titular (Art. 18) — suportados pelo produto
Confirmação da existência de tratamento · acesso · correção · anonimização, bloqueio ou eliminação de dados desnecessários/excessivos · portabilidade · informação sobre compartilhamentos · informação sobre a possibilidade de não consentir · **revogação do consentimento**. (Ver RF-13.)

### 9.5 Dados de crianças e adolescentes (Art. 14)
Tratamento sempre no **melhor interesse** do menor, com **consentimento do responsável** e coleta mínima.

### 9.6 Medidas técnicas e organizacionais (Art. 46–49)
Mapeamento direto entre exigências legais e funcionalidades:

| Exigência LGPD | Medida no produto |
|---|---|
| Segurança e confidencialidade | Criptografia em trânsito/repouso, RBAC, MFA |
| Minimização | Coleta restrita às finalidades; campos opcionais claramente marcados |
| Rastreabilidade | Trilha de auditoria imutável (RF-12) |
| Anonimização para estatística | Relatórios agregados/anonimizados (RF-10) |
| Gestão de consentimento | Termo versionado, registro e revogação (RF-07) |
| Direitos do titular | Acesso, correção, portabilidade, eliminação (RF-13) |
| Retenção e descarte | Políticas de retenção e eliminação/anonimização programadas |
| Resposta a incidentes | Processo de detecção, contenção e **notificação à ANPD e aos titulares** (Art. 48) |

### 9.7 Retenção e descarte (Art. 15 e 16)
- Definir **prazos de retenção** por categoria de dado.
- Ao término da finalidade, **eliminar ou anonimizar**, salvo obrigação legal de guarda ou uso exclusivamente estatístico/anônimo.

### 9.8 Transferência internacional (Art. 33)
- **Evitada por padrão**: hospedagem e backups em infraestrutura situada no **Brasil**.

### 9.9 Documentação de conformidade
- **Registro das operações de tratamento** (Art. 37).
- **Relatório de Impacto à Proteção de Dados Pessoais (RIPD/DPIA)** (Art. 38), recomendado por envolver dados sensíveis.
- Política de Privacidade e Termo de Consentimento publicados e versionados.

---

## 10. Modelo de Dados

### 10.1 Entidades principais

```
Usuário ───< (registra/atualiza) >─── Paciente ───< Necessidade >─── Doação/Atendimento
   │                                      │  │
   │                                      │  └──< Diagnóstico (Cardiopatia)
   │                                      │
   │                                      ├──< Consentimento
   │                                      └──< Anexo (laudo, receita, comprovante)
   │
   └──> Log de Auditoria (todas as ações sobre dados sensíveis)
```

### 10.2 Dicionário de dados (resumo)

**Usuário** — `id` · nome · e-mail · senha (*hash*) · perfil (Administrador/Coordenador/Profissional) · conselho e número (CRM/COREN/CRN/CRESS) · status · MFA · criado_por · datas.

**Paciente** *(titular — dados sensíveis)* — `id` · nome completo · nome social · nascimento · sexo/gênero · CPF *(criptografado)* · CNS/RG · contato · endereço · representante legal · status (ativo/inativo/alta/óbito) · profissional responsável · consentimento_id · datas.

**Diagnóstico (Cardiopatia)** — `id` · paciente_id · descrição · CID-10 · classe NYHA · data do diagnóstico · observações clínicas.

**Necessidade** — `id` · paciente_id · **categoria** (medicamento/produto dietético/exame de alto custo) · **tipo** (ex.: ecocardiograma, angiotomografia, ressonância, cateterismo; nome do medicamento/produto) · prioridade · status · prazo/validade · recorrência · quantidade/unidade · justificativa clínica · profissional solicitante · datas.

**Doação/Atendimento** — `id` · necessidade_id · tipo (item/serviço/agendamento) · doador (identificado/anônimo) · quantidade/valor · status · comprovante · responsável · data.

**Consentimento** — `id` · paciente_id · versão do termo · finalidades · forma de coleta · evidência · status (ativo/revogado) · data e data de revogação · responsável.

**Anexo** — `id` · entidade vinculada · tipo · arquivo (criptografado) · metadados · *hash* · enviado_por · data.

**Log de Auditoria** — `id` · usuário_id · ação · entidade + id · data/hora · IP/dispositivo · resultado.

### 10.3 Catálogos (gerenciáveis pelo administrador)
- **Tipos de exame de alto custo**: Ecocardiograma · Angiotomografia · Ressonância · Cateterismo *(extensível)*.
- **Categorias de necessidade**, **níveis de prioridade**, **status** e **conselhos profissionais**.

---

## 11. Fluxos Principais

### 11.1 Habilitação de profissional
1. Administrador convida profissional (nome, e-mail, perfil).
2. Sistema envia link seguro e temporário.
3. Profissional define senha (e MFA, se exigido) e aceita os termos de uso.
4. Conta ativada; evento registrado na auditoria.

### 11.2 Cadastro de paciente com consentimento
1. Profissional preenche dados de identificação, contato, endereço e diagnóstico.
2. Sistema valida campos obrigatórios e documentos.
3. Profissional registra a **base legal** e coleta o **consentimento** (quando aplicável).
4. Cadastro salvo; auditoria registra autor, data e finalidade.

### 11.3 Registro e busca de necessidade *(fluxo central)*
1. Profissional adiciona necessidade ao paciente (categoria, tipo, prioridade, prazo).
2. Necessidade entra como **Aberta**.
3. Outro profissional usa a **busca por necessidade** (ex.: "ecocardiograma · Crítica · cidade X").
4. Sistema retorna a lista priorizada, com dados sensíveis mascarados.
5. Resultado pode ser salvo como filtro ou exportado (com auditoria).

### 11.4 Atendimento da necessidade
1. Profissional registra doação/atendimento vinculado à necessidade.
2. Ao suprir integralmente, a necessidade passa a **Atendida**; parcialmente, mantém saldo.
3. Comprovante anexado; indicadores atualizados.

### 11.5 Exercício de direitos do titular
1. Solicitação do titular recebida pelo Instituto/DPO.
2. Profissional/administrador localiza o paciente e executa a ação (acesso, correção, portabilidade, eliminação/anonimização ou revogação).
3. Ação registrada com data e responsável.

---

## 12. Arquitetura e Stack Tecnológica

> Recomendações tecnológicas; podem ser ajustadas pela equipe de engenharia conforme disponibilidade e custo.

### 12.1 Visão lógica (camadas)

```
[ Cliente Web Responsivo / PWA ]
            │  HTTPS (TLS)
            ▼
[ API de Aplicação (REST) ]  ──  Autenticação/Autorização (RBAC, MFA)
            │
            ├──> [ Banco de Dados Relacional ]  (dados estruturados, integridade, criptografia de campo)
            ├──> [ Armazenamento de Objetos ]    (anexos criptografados, URLs assinadas)
            └──> [ Serviço de Auditoria/Logs ]   (trilha imutável, monitoramento)
```

### 12.2 Stack recomendada

| Camada | Recomendação | Justificativa |
|---|---|---|
| Cliente | Aplicação web responsiva (PWA) | Sem instalação por loja, acessível em qualquer dispositivo |
| API | Serviço *stateless* com API REST e autenticação por token | Simplicidade, segurança e escalabilidade |
| Banco de dados | Relacional (ex.: PostgreSQL) | Integridade referencial, criptografia de campo, controle por linha |
| Anexos | Armazenamento de objetos com criptografia e URLs assinadas | Segurança e baixo custo |
| Hospedagem | Provedor com **região no Brasil** | Evita transferência internacional (LGPD) |
| Observabilidade | Monitoramento de erros, desempenho e disponibilidade | Operação confiável |

### 12.3 Segurança de infraestrutura
- Segregação de ambientes (desenvolvimento, homologação, produção).
- Gestão de segredos fora do código; rotação de chaves.
- Backups criptografados e testados; princípio do menor privilégio nas credenciais de serviço.
- Integração contínua com verificação automática de segurança e testes.

---

## 13. Identidade Visual e Design System

A identidade segue a **logomarca do Instituto Corações em Rede**: um coração em tons quentes de vermelho e laranja, com a palavra "CORAÇÕES" em vermelho-vinho profundo. A paleta transmite **acolhimento, vitalidade e cuidado**.

### 13.1 Paleta de cores (derivada da logomarca)

#### Cores de marca

| Token | Nome | HEX | Uso |
|---|---|---|---|
| `--cor-primaria` | Vermelho Coração | `#E63329` | Ações principais, destaques, identidade |
| `--cor-primaria-escura` | Vermelho Profundo | `#C82D20` | Estados *hover/active*, contraste de botões |
| `--cor-secundaria` | Vinho Corações | `#6E1A14` | Títulos, textos de marca, rodapé, áreas escuras |
| `--cor-acento` | Laranja Vivo | `#F47A21` | Acentos, destaques secundários, prioridade "Alta" |
| `--cor-acento-claro` | Coral Claro | `#FBE0DD` | Fundos suaves, realces de seleção |

#### Neutros

| Token | HEX | Uso |
|---|---|---|
| `--neutro-900` | `#1F2123` | Texto principal |
| `--neutro-700` | `#3F4346` | Texto forte |
| `--neutro-500` | `#6B7075` | Texto secundário |
| `--neutro-300` | `#C9CDD2` | Bordas e divisores |
| `--neutro-100` | `#F2F4F6` | Fundo de tela |
| `--branco` | `#FFFFFF` | Superfícies, cartões |

#### Cores semânticas (status)

| Significado | HEX (base) | Fundo | Observação |
|---|---|---|---|
| Sucesso | `#2E7D4F` | `#E3F2EA` | Confirmações |
| Atenção | `#B26A00` | `#FCEFD6` | Avisos e prazos próximos |
| Erro | `#B3261E` | `#FBE6E4` | Erros e validações |
| Informação | `#1565C0` | `#E3EEFB` | Mensagens neutras |

> **Acessibilidade:** o status nunca é comunicado **apenas por cor** — sempre acompanhado de ícone e/ou rótulo textual. Os valores devem ser validados em verificador de contraste para atender **WCAG 2.1 AA**; para botões com o Vermelho Coração, usar texto branco em tamanho adequado ou o **Vermelho Profundo** para garantir contraste suficiente.

#### Indicadores de prioridade da necessidade

| Prioridade | Cor | Token |
|---|---|---|
| Crítica | `#C82D20` (vermelho profundo) | `--prio-critica` |
| Alta | `#F47A21` (laranja) | `--prio-alta` |
| Média | `#F4A91E` (âmbar) | `--prio-media` |
| Baixa | `#2E7D4F` (verde) | `--prio-baixa` |

### 13.2 Tipografia
- **Títulos/Destaque:** fonte sem serifa, geométrica e amigável (ex.: *Montserrat* ou *Poppins*), em peso semibold/bold, ecoando a logomarca.
- **Texto/Interface:** fonte sem serifa de alta legibilidade (ex.: *Inter* ou *Source Sans 3*).
- **Corpo mínimo:** 16 px; entrelinha ~1,5; hierarquia clara de tamanhos.

### 13.3 Componentes e diretrizes
- **Cartão de paciente** com nome, idade, cidade, **etiquetas de necessidade** e prioridade.
- **Etiquetas (badges)** coloridas para categoria de necessidade e prioridade.
- **Formulários** com rótulos sempre visíveis, validação inline e mensagens claras.
- **Tabelas/listas** com mascaramento de dados sensíveis e ações contextuais por perfil.
- **Botões**: primário (Vermelho Coração), secundário (contorno vinho), terciário (texto).
- Espaçamento em grade de 8 px; cantos suavemente arredondados; sombras discretas.

### 13.4 Tom e voz
Acolhedor, humano, claro e respeitoso. Evita jargão técnico e expressões que reduzam a dignidade do paciente. Mensagens orientam a próxima ação de forma objetiva.

> Os *tokens* de cor estão disponíveis em `docs/assets/design-tokens.css` para uso direto na interface.

---

## 14. Acessibilidade

O produto busca conformidade com **WCAG 2.1, nível AA**:
- **Contraste** de texto e componentes validado (mínimo 4,5:1 para texto normal; 3:1 para texto grande e elementos de interface).
- **Navegação completa por teclado** e **foco visível**.
- Compatibilidade com **leitores de tela** (rótulos, *landmarks* e textos alternativos).
- **Alvos de toque ≥ 44×44 px** e suporte a aumento de fonte.
- Informação nunca transmitida **apenas por cor**.
- Formulários com rótulos associados e mensagens de erro descritivas.

---

## 15. Roadmap e Fases de Entrega

### Fase 0 — Descoberta e Conformidade
Definição das bases legais com o DPO, **RIPD/DPIA**, termo de consentimento, política de privacidade, arquitetura e identidade visual.

### Fase 1 — MVP
Autenticação/RBAC · gestão de usuários pelo administrador · cadastro de pacientes e diagnóstico · **registro de necessidades** · **busca e filtros por necessidade** · consentimento · trilha de auditoria · web responsivo (PWA).

### Fase 2 — Operação ampliada
Atendimento de necessidades/doações · anexos · relatórios e indicadores · notificações.

### Fase 3 — Expansão
Portal para doadores/parceiros · integrações externas · melhorias de uso *offline* · novos relatórios.

---

## 16. Riscos e Mitigações

| Risco | Impacto | Mitigação |
|---|---|---|
| Vazamento de dados sensíveis | Alto | Criptografia, RBAC, MFA, auditoria, RIPD, testes de segurança |
| Não conformidade com a LGPD | Alto | Bases legais documentadas, consentimento, retenção, DPO atuante |
| Baixa adoção pelos profissionais | Médio | Interface simples, treinamento, fluxos curtos, suporte |
| Qualidade inconsistente do cadastro | Médio | Validações, campos obrigatórios, catálogos padronizados |
| Dependência de poucos voluntários | Médio | Documentação, papéis claros, base centralizada |
| Expansão de escopo não planejada | Médio | Escopo do MVP fechado, roadmap por fases |
| Custo de infraestrutura | Baixo | Stack enxuta, provedor com região no Brasil, monitoramento de custos |

---

## 17. Definição de Pronto (Definition of Done)

Uma funcionalidade é considerada concluída quando:
- Atende a todos os **critérios de aceite** do requisito.
- Possui **testes automatizados** e foi validada manualmente.
- Respeita **RBAC, auditoria e privacidade** (mascaramento, mínimos privilégios).
- Está **acessível (WCAG 2.1 AA)** e responsiva.
- Não introduz dados sensíveis em logs em texto claro.
- Documentação e textos de interface em **pt-BR** revisados.
- Aprovada em revisão de código e de segurança.

---

## 18. Questões em Aberto

| # | Questão | Responsável |
|---|---|---|
| Q1 | Confirmar bases legais definitivas para cada finalidade de tratamento. | DPO / Jurídico |
| Q2 | Haverá migração de dados de planilhas existentes? Em que formato? | Instituto / Engenharia |
| Q3 | O Coordenador será ativado no MVP ou em fase posterior? | Direção |
| Q4 | Catálogo inicial de medicamentos e produtos dietéticos mais frequentes. | Coordenação Clínica |
| Q5 | Provedor de hospedagem e responsável técnico pela operação. | Engenharia |
| Q6 | Política de retenção por categoria de dado. | DPO |

---

## 19. Glossário

| Termo | Definição |
|---|---|
| **Cardiopatia** | Doença que acomete o coração ou o sistema cardiovascular. |
| **CID-10** | Classificação Internacional de Doenças (10ª revisão). |
| **NYHA** | Classificação funcional de insuficiência cardíaca (classes I a IV). |
| **CNS** | Cartão Nacional de Saúde. |
| **LGPD** | Lei Geral de Proteção de Dados Pessoais (Lei nº 13.709/2018). |
| **ANPD** | Autoridade Nacional de Proteção de Dados. |
| **Controlador / Operador** | Quem decide sobre o tratamento / quem o executa em seu nome. |
| **Encarregado (DPO)** | Pessoa que atua como canal entre titulares, organização e ANPD. |
| **Dado pessoal sensível** | Inclui dados de saúde; exige proteção reforçada (LGPD, Art. 11). |
| **RIPD/DPIA** | Relatório de Impacto à Proteção de Dados Pessoais. |
| **RBAC** | Controle de acesso baseado em papéis. |
| **MFA** | Autenticação multifator. |
| **PWA** | Aplicação web instalável, com experiência próxima à de um app. |
| **RPO / RTO** | Perda máxima de dados tolerável / tempo máximo de recuperação. |
| **WCAG** | Diretrizes de acessibilidade para conteúdo web. |

---

## 20. Anexos

### Anexo A — Catálogo inicial de necessidades

**Exames de alto custo (tipos iniciais):**
- Ecocardiograma
- Angiotomografia
- Ressonância
- Cateterismo

**Medicamentos:** lista a ser construída com a Coordenação Clínica (campo aberto com princípio ativo, dosagem e posologia).

**Produtos dietéticos:** lista a ser construída com a Coordenação Clínica (tipo, descrição e periodicidade).

### Anexo B — Termo de Consentimento (rascunho a validar pelo Jurídico/DPO)

> *"Autorizo o Instituto Corações em Rede a tratar meus dados pessoais e de saúde com a finalidade de cadastro, acompanhamento das minhas necessidades e mobilização de doações que me beneficiem, nos termos da Lei nº 13.709/2018 (LGPD). Fui informado(a) sobre as finalidades, sobre meus direitos como titular e sobre o canal de contato do Encarregado de Dados. Estou ciente de que posso revogar este consentimento a qualquer momento."*
>
> Versão do termo · Data · Identificação do titular ou responsável legal · Evidência de aceite.

---

*Documento elaborado segundo boas práticas de engenharia de software para aplicações da área da saúde, com foco em segurança, privacidade e conformidade legal.*
