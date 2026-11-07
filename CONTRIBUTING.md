# Guia de contribuição

Este documento define como o código entra no repositório do homebroker. Leia antes de abrir sua primeira branch.

## Branches

| Branch | Para que serve | Commit direto? |
|---|---|---|
| `main` | Código estável. Recebe apenas o que já foi validado na `develop`. | Não, bloqueado pela proteção do repositório |
| `develop` | Integração das funcionalidades em desenvolvimento. É a branch padrão do repositório. | Não, bloqueado pela proteção do repositório |
| `feature/*` | Onde o desenvolvimento acontece de fato. | Sim |

Toda alteração, seja uma funcionalidade nova, uma correção ou uma remoção, nasce em uma branch `feature/` criada a partir da `develop` atualizada.

### Nome da branch

Padrão: `feature/HB-<n>_descricao-curta`

- `HB-<n>` é o número da issue que a branch resolve
- A descrição é curta, em letras minúsculas, com hífen no lugar de espaço e sem acentos

Exemplos:

- `feature/HB-2_fluxo-git`
- `feature/HB-6_dominio-ativo`

Evite:

- `feature/ativo` (sem o número da issue)
- `feature/HB-6_Criação do Ativo` (maiúsculas, acento e espaço)

## Commits

Padrão: `HB-<n>: descrição no presente`

Exemplos:

- `HB-6: adiciona validação de ticker`
- `HB-7: corrige débito com valor igual ao saldo`

Evite mensagens vagas como `ajustes`, `wip` ou `agora vai`.

Prefira commits pequenos, cada um com uma única mudança. Fica mais fácil de revisar e, se algo quebrar, de descobrir onde.

## Pull Requests

### Da feature para a develop

- Todo PR de feature tem como destino a `develop`
- A descrição segue o template do repositório e inclui `Closes #<n>`, para a issue fechar automaticamente no merge
- PR com código precisa vir acompanhado de testes
- O build precisa estar passando
- **Estratégia de merge: squash.** Cada issue vira um único commit na `develop`, deixando o histórico limpo e fácil de ler

### Da develop para a main

- Quando a `develop` tiver um conjunto estável de entregas, normalmente ao fim de cada fase do roadmap, é aberto um PR da `develop` para a `main`
- **Estratégia de merge: merge commit, sem squash.** Assim a `main` preserva os commits de cada issue e as duas branches continuam com o mesmo histórico. Um squash aqui juntaria várias issues em um commit só e faria a `main` e a `develop` divergirem

## Fluxo resumido

1. Atualize a `develop` local
2. Crie a branch `feature/HB-<n>_descricao-curta` a partir dela
3. Desenvolva com commits pequenos seguindo o padrão
4. Publique a branch e abra o PR para a `develop`
5. Aguarde a revisão e faça os ajustes pedidos
6. Faça o merge com squash. A branch é apagada automaticamente