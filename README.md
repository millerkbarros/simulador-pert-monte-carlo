# 📊 Simulador de Prazos de Projetos — PERT + Monte Carlo

Ferramenta web para estimar **a probabilidade de entregar um projeto no prazo**, combinando a técnica **PERT** (estimativa de três pontos) com a **Simulação de Monte Carlo**.

🔗 **Acesse:** https://millerkbarros.github.io/simulador-pert-monte-carlo/

## O que a ferramenta faz

- Cadastra as etapas do projeto com estimativas **Otimista (O)**, **Mais provável (M)** e **Pessimista (P)**.
- Calcula o **PERT** de cada etapa: `TE = (O + 4 × M + P) ÷ 6`.
- Roda **milhares de simulações** de Monte Carlo para gerar cenários possíveis de entrega.
- Considera apenas as etapas **a partir do marco inicial** escolhido (ex.: a partir do Desenvolvimento). O marco funciona como **linha de base**: mantido fixo, permite comparar o prazo realizado com o previsto e medir atrasos.
- Mostra a **probabilidade de cumprir o prazo** e os percentis **P50, P80 e P90**.
- Com a **data de início do marco** (opcional), converte cada indicador em **data de conclusão prevista**, pulando fins de semana e feriados nacionais quando a unidade é dias úteis.
- Exibe histograma e curva acumulada de probabilidade (CDF).
- Exporta o resultado em **PDF** e **CSV**, e salva configurações no próprio navegador.

## Como usar

1. Preencha nome do projeto, Analista Funcional, Fornecedor e o prazo disponível a partir do marco (em dias úteis ou corridos).
2. Cadastre as etapas com os valores O, M e P (regra: O ≤ M ≤ P).
3. Escolha o **marco inicial** e a distribuição estatística.
4. Clique em **Executar / recalcular Monte Carlo**.
5. Use o **P80** como referência de planejamento e o **P90** como referência conservadora.

## Distribuições disponíveis

| Distribuição | Comportamento |
|---|---|
| **Beta-PERT (λ=4)** | Concentra os sorteios perto do valor mais provável (M). É o padrão do PERT. |
| **Triangular** | Espalha mais os sorteios entre O e P. Gera cenários mais dispersos. |

## Premissas do modelo

- As etapas são executadas **em sequência** (sem paralelismo).
- A duração de cada etapa é sorteada **de forma independente**. Quando as etapas compartilham riscos (mesma equipe ou fornecedor), os atrasos tendem a ocorrer juntos e o risco real pode ser maior. Nesses casos, prefira o **P90**.
- Os resultados são exibidos em **dias inteiros**: os percentis **P50, P80 e P90 são sempre arredondados para cima** (qualquer fração vira um dia a mais, para não prometer prazo menor que o calculado); PERT e média usam arredondamento comum (a partir de 0,5 para cima). Por ser uma simulação, uma nova execução pode, raramente, variar em 1 dia.

## Privacidade

Tudo roda **no navegador**: nenhum dado é enviado para servidor. As simulações salvas ficam no `localStorage` do navegador/dispositivo usado.

## Tecnologia

Página única em **HTML5, CSS e JavaScript puro**, sem dependências externas.

## Portfólio profissional

Organizei uma visão dos projetos, abordagens de trabalho e conteúdos técnicos publicados no LinkedIn, incluindo o simulador PERT + Monte Carlo, o framework PALAVRA, o framework VITREX e experiências em projetos de TI.

➡️ **[Acesse o portfólio profissional](PORTFOLIO.md)**

---

Criado por **Miller Cardoso Barros**.
