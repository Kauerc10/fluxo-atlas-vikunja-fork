# Fluxo Atlas

O ramo `atlas-public` parte do [Vikunja v2.7.1](https://github.com/go-vikunja/vikunja/tree/v2.7.1). Ele inclui a exibição do **Valor do mês** nos cartões do Kanban mensal do Financeiro. Consulte a [licença original](LICENSE).

O Gitleaks verifica os commits do Atlas e os pull requests direcionados a `atlas-public`. Antes de publicar uma alteração, rode a mesma verificação no histórico local.

```sh
gitleaks git --redact=100 --log-opts "v2.7.1..HEAD" .
```

O fork contém código-fonte. Mantenha credenciais, dados de clientes e configurações de produção fora deste repositório.
