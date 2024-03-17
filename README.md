# ZAP Report

Durante a análise de segurança realizada com a ferramenta OWASP ZAP (Zed Attack Proxy), foram identificados alguns problemas em nossa aplicação. Este relatório destaca os problemas encontrados e apresenta as soluções propostas para mitigá-los.

## Listar/exibir cardápio

| Report antes | Resport depois |
| ------------ | ---------------|
| [Click aqui](zap-report-cardapio-antes.html)   | [Click aqui](zap-report-cardapio-depois.html)     |

### 1. X-Content-Type-Options Header Missing

#### Descrição:

A ausência do cabeçalho X-Content-Type-Options nas respostas HTTP pode expor a aplicação a riscos de segurança relacionados à detecção inadequada do tipo MIME pelos navegadores.

#### Impacto Potencial:

Risco de execução de scripts maliciosos ou carregamento de conteúdo não seguro devido à detecção de tipo MIME inadequada.

#### Solução Proposta:

Adicionar o cabeçalho X-Content-Type-Options: nosniff em todas as respostas HTTP para instruir o navegador a não realizar a detecção de tipo MIME.

### 2. Spring Actuator Information Leak:

Descrição: Os atuadores do Spring, como o /actuator/health, podem expor informações sensíveis sobre o estado da aplicação, incluindo detalhes sobre saúde e configuração. 

#### Impacto Potencial:

Exposição indevida de informações sensíveis, o que pode facilitar ataques de exploração e comprometer a segurança da aplicação.

#### Solução Proposta:

Desabilitar os atuadores de saúde e outros atuadores desnecessários ou restringi-los apenas a usuários administrativos para evitar vazamentos de informações.

## Realização pedido (Checkout)

| Report antes | Resport depois |
| ------------ | ---------------|
| Click aqui   | Click aqui     |

### 1. X-Content-Type-Options Header Missing

#### Descrição:

A ausência do cabeçalho X-Content-Type-Options nas respostas HTTP pode expor a aplicação a riscos de segurança relacionados à detecção inadequada do tipo MIME pelos navegadores.

#### Impacto Potencial:

Risco de execução de scripts maliciosos ou carregamento de conteúdo não seguro devido à detecção de tipo MIME inadequada.

#### Solução Proposta:

Adicionar o cabeçalho X-Content-Type-Options: nosniff em todas as respostas HTTP para instruir o navegador a não realizar a detecção de tipo MIME.

### 2. Buffer Overflow

#### Descrição:

Buffer overflow é um erro caracterizado pela sobregravação de espaços de memória do processo web de fundo, que nunca deveriam ser modificados intencional ou inadvertidamente. A sobregravação de valores dos registradores IP (Instruction Pointer), BP (Base Pointer) e outros causa exceções, falhas de segmentação e outros erros de processo. Geralmente, esses erros encerram a execução da aplicação de maneira inesperada.

#### Impacto Potencial:

A ocorrência de buffer overflow pode resultar na execução inesperada da aplicação, levando a comportamentos não previstos, falhas de segurança e até mesmo a comprometimento do sistema. Os invasores podem explorar esse erro para executar código arbitrário, comprometer a integridade dos dados ou até mesmo assumir o controle do sistema.

#### Solução Proposta:

Para solucionar o problema de buffer overflow, foi realizada uma revisão do código-fonte, removendo erros genéricos que ocorriam quando os dados eram informados em formatos diferentes do tipo esperado. Além disso, foram implementadas validações adicionais para garantir o tamanho correto dos dados inseridos. Essas ações ajudaram a mitigar o risco de buffer overflow e fortalecer a segurança da aplicação.

## Confirmação do Pagamento (Webhook)

| Report antes | Resport depois |
| ------------ | ---------------|
| Click aqui   | Não disponível |

Para este projeto nenhum problema foi encontrado, uma vez que as melhorias propostas pelos outros reports foram tambem realizar nele.