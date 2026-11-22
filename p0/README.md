# Gerador Inteligente de Templates DOCX (P0)

Este repositório contém a entrega final do período P0 para o curso Trends IA. O projeto é um gerador de
templates para a produção de documentos em lote que utiliza Inteligência Artificial.

## Problema Escolhido

A criação em lote de documentos (mala direta, convites, faturas, notificações, etc.) frequentemente
esbarra nas limitações de ferramentas tradicionais, como o recurso *[mail merge][mail_merge]* do
Microsoft Word. Ferramentas padrão têm dificuldade em lidar com concordância gramatical dinâmica
(evitando os incômodos "Prezado aluno(a)" ou "a(s) pendência(s)") e com regras de negócio complexas.

A biblioteca `python-docx-template` resolve essa limitação ao unir o Microsoft Word à linguagem de
templates Jinja, permitindo a criação de documentos muito mais exclusivos e adaptados (ex: inserir um
parágrafo de desconto apenas se o cliente atender a determinados requisitos). O grande gargalo, no
entanto, é a barreira técnica: a sintaxe do Jinja não é acessível para leigos. O problema central do
projeto é **como permitir que usuários sem conhecimento em programação utilizem o poder do Jinja e do
`python-docx-template` por meio de uma interface simples.**

O escopo dessa solução é apenas criar o template, com base em documentos já existentes do usuário e
instruções em linguagem natural, de forma que seja um primeiro passo para o desenvolvimento de uma
interface gráfica voltada ao usuário final.

## Usuário e Público-Alvo

Profissionais administrativos, secretarias de escolas/universidades, departamentos de Recursos Humanos,
escritórios de advocacia e equipes de cobrança ou vendas. Em suma, **qualquer pessoa que precise
automatizar a geração de documentos em lote com alta personalização**, mas que não possui conhecimento
técnico para escrever códigos e regras condicionais em Jinja.

## Justificativa para Utilizar um LLM

Poderia-se pensar em utilizar o LLM para escrever e gerar todos os documentos finais de uma vez.
Contudo, essa abordagem apresenta falhas críticas:

1. **Risco de Alucinação:** O modelo baseia-se em escolhas estatísticas, o que exigiria revisão humana
manual em *cada documento gerado* para garantir que dados de faturamento, nomes ou cobranças não foram
inventados ou alterados.
2. **Custo Computacional e Financeiro:** Gerar milhares de documentos inteiros usando prompts seria
extremamente lento e custoso.

A melhor solução arquitetural é **usar o LLM exclusivamente para gerar o template Jinja** a partir das
instruções em linguagem natural do usuário. O LLM atua apenas como um tradutor de intenção (da linguagem
humana para a sintaxe do Jinja). Uma vez que o template correto é gerado, a renderização dos milhares de
documentos finais fica a cargo do `python-docx-template` de forma estritamente determinística, rápida,
barata e sem margem para alucinações estatísticas nos dados. Modelos preditivos tradicionais ou outras
IAs não são adequados aqui pois não possuem a capacidade de generalização e compreensão de linguagem
natural necessárias para escrever código Jinja sob demanda.

## Funcionamento da Solução

*A ser documentado nas próximas iterações.* A premissa básica será uma interface onde o usuário faz o
upload de uma base de dados (ex: Excel/CSV), de documentos já produzidos e escreve o que deseja em
linguagem natural. A solução orquestrará a criação do template DOCX com as tags Jinja.

## Limites do Projeto

Nesta etapa de concepção, delimitamos que:

- A ferramenta atua na camada de transformação de texto (Prompt para Jinja). Não resolverá formatações
visuais altamente complexas que não possam ser ancoradas no template base do Word.
- A acurácia do template Jinja gerado dependerá da clareza das instruções do usuário sobre as regras de
negócio desejadas.
- O processamento em lote é restrito a arquivos suportados pela biblioteca `.docx`. Conversões nativas
para outros formatos (como PDF) fora da renderização padrão estão além do escopo inicial deste MVP.

---

### *Seções a serem preenchidas nas próximas entregas (Detalhes de Implementação e Testes):*

## Instalação

*(Em desenvolvimento)*

## Configuração do Acesso ao LLM e Indicação dos Testes

*(Em desenvolvimento)*

## Execução

*(Em desenvolvimento)*

## Exemplos de Entrada e Saída

*(Em desenvolvimento)*

## Execução dos Testes

*(Em desenvolvimento)*

## Limitações Conhecidas (Técnicas)

*(Em desenvolvimento)*

## Link para o Vídeo

*(A ser gravado na entrega final)*

[mail_merge]: https://support.microsoft.com/pt-br/word/use-mail-merge-for-bulk-email-letters-labels-and-envelopes
