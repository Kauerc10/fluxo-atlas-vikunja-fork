# Fluxo Atlas

O Fluxo Atlas é a adaptação do [Vikunja](https://github.com/go-vikunja/vikunja) que usamos para acompanhar o trabalho de um cartório. A equipe usa os quadros Kanban para organizar atendimentos e acompanhar as etapas de setores como Procurações, Ata Notarial e Financeiro. Este fork reúne os ajustes de código feitos a partir das necessidades dessa rotina.

## Por que mantemos um fork

O Vikunja já oferece a base para o trabalho diário, com projetos, tarefas, responsáveis, prazos e quadros Kanban. Algumas necessidades do cartório surgem no uso desses mesmos recursos. No Financeiro, por exemplo, a responsável precisa conferir valores de várias contas de uma vez enquanto acompanha a cobrança do mês. Abrir cada cartão para ler o valor torna essa conferência mais demorada.

O fork permite fazer ajustes pontuais sobre uma versão conhecida do Vikunja e registrar quais mudanças entraram em cada edição do Fluxo Atlas. A base atual é a [v2.7.1 oficial](https://github.com/go-vikunja/vikunja/tree/v2.7.1). Os quadros, as contas e as rotinas mensais pertencem à configuração da instância do cartório.

## O que adaptamos

### Valor do mês no cartão do Financeiro

O Financeiro acompanha valores a receber de clientes frequentes que acumulam serviços e quitam o total do mês. Cada conta tem um cartão no quadro mensal.

1. Abra o cartão no quadro do mês, por exemplo **11/2026**.
2. Preencha a primeira linha da descrição no formato `Valor do mês: R$ 1.250,00` e salve.
3. Volte ao Kanban. O valor aparece abaixo do nome da conta e acompanha o cartão quando ele muda de coluna. Se o campo estiver vazio, a linha fica oculta.

O nome da conta permanece como título, e o valor é registrado em um só lugar. A regra atual identifica os subprojetos mensais pelo ID do projeto pai Financeiro e pelo formato `MM/AAAA`. Em outra instância, o ID precisa ser ajustado no código. A seleção de campos por quadro ainda não está disponível na interface. [Componente do cartão](frontend/src/components/tasks/partials/KanbanCard.vue)

### Vikunja Desktop no Windows

A equipe também usa o Vikunja instalado no Windows. Na edição **2.7.1-atlas.2**, o Desktop passou a remover o cache de atualização antigo ao iniciar. Isso recupera perfis que podiam ficar com a tela branca quando o cache apontava para arquivos de uma edição anterior. A edição inclui o ícone da lhama no executável empacotado. [Código-fonte da edição Desktop](https://github.com/Kauerc10/fluxo-atlas-vikunja-fork/tree/2.7.1-atlas.2-source)

## Código e manutenção

- **Base e documentação oficial** · Consulte o [README original do Vikunja v2.7.1](https://github.com/go-vikunja/vikunja/blob/v2.7.1/README.md) para instalação, compilação e contribuição ao projeto original.
- **Histórico do Atlas** · A branch `atlas-public` reúne as alterações públicas. O [registro técnico](FLUXO-ATLAS.md) documenta a base e a verificação local.
- **Segurança** · O [Gitleaks](https://github.com/Kauerc10/fluxo-atlas-vikunja-fork/actions/workflows/atlas-gitleaks.yml) verifica os commits do Atlas em pushes e pull requests para `atlas-public`. Este fork público reúne código-fonte e documentação. Credenciais, dados do cartório e configurações de produção são mantidos fora dele.
- **Licença** · O código deriva do trabalho dos mantenedores e colaboradores do Vikunja e segue as licenças do projeto. Veja a [licença principal](LICENSE) e a [licença do Desktop](desktop/LICENSE).
