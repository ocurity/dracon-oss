# Smithy (formerly Dracon)

<p align="center">
  <img alt="dracon-logo-dark-mode" src="assets/dracon-logo-light.svg#gh-dark-mode-only"/>
</p>
<p align="center">
  <img alt="dracon-logo-light-mode" src="assets/dracon-logo-dark.svg#gh-light-mode-only"/>
</p>

By [Smithy](https://smithy.security)

Security scanning,results unification and enrichment tool
([ASOC](https://www.gartner.com/reviews/market/application-security-orchestration-and-correlation-asoc-tools))

Security pipelines on Kubernetes. The purpose of this project is to provide a
scalable and flexible framework to execute arbitrary security scanning
tools on code and infrastructure while processing the results in a versatile
way.

```mermaid
flowchart LR
    S["Code Setup & Build"]

    P_GoSec["Producer - GoSec (Golang)"]
    P_SecBugs["Producer - SpotBugs (Java)"]
    P_Bandit["Producer - Bandit (Python)"]
    P_TFSec["Producer - TFSec (Terraform)"]

    P_Aggregator["Producer - Results Aggregation"]

    E_Deduplication["Enricher - Deduplication"]
    E_Policy["Enricher - Policy"]
    E_Aggregator["Enricher - Enriched Results Aggregator"]

    C_Slack["Consumer - Slack"]
    C_Elasticsearch["Consumer - Elasticsearch"]
    C_Jira["Consumer - Jira"]

    S-->P_TFSec
    S-->P_GoSec
    S-->P_SecBugs
    S-->P_Bandit

    P_TFSec-->P_Aggregator
    P_GoSec-->P_Aggregator
    P_SecBugs-->P_Aggregator
    P_Bandit-->P_Aggregator

    P_Aggregator-->E_Deduplication
    P_Aggregator-->E_Policy

    E_Policy-->E_Aggregator
    E_Deduplication-->E_Aggregator

    E_Aggregator-->C_Slack
    E_Aggregator-->C_Elasticsearch
    E_Aggregator-->C_Jira


```

## Announcements!!!

We have renamed the team and the project to Smithy. Come join us at our updated [Github repository](https://github.com/smithy-security/smithy) and help us build more awesome stuff!
You can also find us on our [Discord server](https://discord.gg/xzsHxUxK).
