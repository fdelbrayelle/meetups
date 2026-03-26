---
title: Data Days Lille 2026 (EN)
---

# Data Days Lille 2026

![Data Days Lille 2026](../entree.jpg)

[Data Days Lille 2026 Programme](https://days.data-lille.fr/2026/fr/programme/)

**Bold passages highlight potential areas for improvement.**

## Intro

10 years ago, a few students from Polytech Lille started a big data meetup.
Here we go for a new edition.
Goal of the association: promote data usage, create meetups, dozens of participants, ...

## Can AI kill collective intelligence? What research tells us (Olivier Nguyen Quoc)

## Sovereign datalake: dbt-duckdb in k8s, a sovereign data lakehouse handcrafted @OrangeB2B! (Antoine Giraud and Cedric OLIVIER)

## The war of orchestrators: Airflow VS Kestra (Florian Deze and Guillaume Fauvergue)

[Link to the presentation](https://days.data-lille.fr/2026/fr/presentations/la-guerre-des-orchestrateurs-airflow-vs-kestra/)

Discussion at the beginning with the speakers, they use Kestra at LMFR. The idea of their talk is to share feedback on their daily use of both Airflow and Kestra as data engineers.

Why this talk? Lots of real-world experience: one flow crashed the others, why won't my DAG run anymore?
We realize these tools are relatively recent.
Many users who preferred Kestra were using the Airflow 1 beta.

What is an orchestrator? Running a sequence of tasks, basically. Not just a cron. Some try to specialize. A DAG is made of tasks. Airflow created by Airbnb in 2016. The talk covers version 3.1. Kestra created by Ludovic Dehon at LMFR, OSS release 2022, talk version 1.3.

Disclaimer: Performance is not the only criterion.

Our topic is developer experience. The idea is not to compare plugins & integrations but how to create flows on a daily basis.

## How to build a flow without wanting to throw my PC out the window?

Example: A file arrives in BLOB storage. Ingestion into Data Warehouse.

## DAG comparison: Airflow / Kestra

Airflow long DAG in Python: code flexibility, important deferrable=True, explicit dependency.

Kestra: flow with a GCS trigger and a BigQuery Load: native event-driven, automatic context passing, built-in cleanup.

Response to the Python vs YAML syntax debate: for the speaker, a data engineer is still a developer and should know Python (opinion).
Going from YAML with ":" to "=" and adding {}. For him it's just a matter of syntax. Saying that Airflow is in Python and therefore refusing is not a valid argument for him.

## Trigger and dependency: how to trigger my flows?

In Kestra: trigger a flow with cron, API call / webhook, flow subscription, sub-flow trigger, event-driven trigger.

In Airflow: trigger a DAG with cron, API call, assets (e.g. datasets), cron & assets mix (a little jab because I was there, they told the audience and I had told them beforehand that we had assets in the EE version), **MessageQueueTrigger (Airflow 3 novelty: "this is where Kestra had its advantage until now")**.

## Run: how to manage my flows?

Presentation of the Kestra dashboard and specifically flow execution (the crux of the matter), presentation of filters, then specific execution with flow overview, run duration, 6 action buttons (restart, replay, pause, force run, API, delete). Gantt chart and logs also shown.

In Airflow: how to find anomalies in DAGs? DAG list (run chart, filter by status, by tag = appreciated feature...). Execution screen with state filter. Specific execution: chart with lineage, click on problematic task to view logs.

**Kestra is preferred here for its filtering system.**

## Maintainability: how to upgrade without issues?

In Airflow:
"The version of an orchestrator is not the version of an operator". Airflow Operator ~= Kestra Plugin.
Example: 500 DAGs use operator "X". If operator X has a breaking change, I have to modify 500 DAGs!
Never use native operators but KubernetesPodOperator and apply **Policies (= "I didn't find this in Kestra"**, operators can be banned or blocked and you can force users to use certain operators).

In Kestra:
It's more complicated to make a plugin wrapper.
You can use sub flows for redundant tasks.
Set default values on arguments (pluginDefaults).
Create your own plugin in Java / Micronaut.
Run a plugin via its own Kestra Docker image.

## Conclusion: who wins?

Each has its pros and cons:

![Conclusion Airflow vs Kestra](../conclusion.jpg)

Airflow:
- Simple operator customization
- Standardized DAG definition via policies
- Versioning per run
- Easier version upgrades (if best practices are followed)

Kestra:
- More complete event-driven trigger types
- CI/CD: Terraform and flow updates with low latency
- More readable syntax for simple flows
- Better designed run management

## Questions

Why not Dagster or Prefect? Not enough experience to answer but challengers are coming and propose to address what Airflow doesn't do.

Is there multi-tenancy in Airflow and Kestra? I directly answered that Kestra offers this and what it brings (but EE feature).

Another person in the audience mentioned [Windmill](https://www.windmill.dev/), a French tool that looks interesting.

---

References:
- [Kestra vs Airflow](https://kestra.io/vs/airflow)
- [Kestra Enterprise Governance Assets](https://kestra.io/docs/enterprise/governance/assets)
