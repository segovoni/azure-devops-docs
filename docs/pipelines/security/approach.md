---
title: Plan an approach to secure your YAML pipelines
description: Apply security recommendations incrementally in your YAML pipelines. Incremental improvements add up.
ms.assetid: a506a55a-2379-4d14-a52c-f4c28abae0ec
ms.reviewer: vijayma
ms.date: 10/27/2023
monikerRange: '> azure-devops-2019'
---

# Plan how to secure your YAML pipelines

[!INCLUDE [version-gt-eq-2020](../../includes/version-gt-eq-2020.md)]

We recommend that you use an incremental approach to secure your pipelines.
Ideally, you would implement all of the guidance that we offer.
But don't be daunted by the number of recommendations.
And don't hold off making *some* improvements just because you can't make all the changes right now.

## Security recommendations depend on each other

Security recommendations have complex interdependencies.
Your security posture depends heavily on which recommendations you choose to implement.
The recommendations that you choose, in turn, depend on the concerns of your DevOps and security teams. 
They also depend on the policies and practices of your organization.

You might choose to tighten security in one critical area and accept less security but more convenience in another area.
For example, if you use [`extends` templates](templates.md#step-targets) to require all builds to run in containers, then you might not need a [separate agent pool for each project](infrastructure.md#separate-agents-for-each-project).

## Begin with a nearly empty template

A good place to start is by enforcing extension from a nearly empty template.
This way, as you start to apply security practices, you have a centralized place that already catches every pipeline.

For more information, see [Templates](templates.md).

:::moniker range=">= azure-devops-2022"

## Disable creation of classic pipelines

:::moniker-end

:::moniker range="=azure-devops-2022"

[!INCLUDE [feature-added-2022-1](../../includes/feature-added-2022-1.md)]

:::moniker-end

:::moniker range=">= azure-devops-2022"

If you develop *only* YAML pipelines, disable creation of classic build and release pipelines. Doing so prevents a security concern that stems from YAML and classic pipelines sharing the same resources, for example the same service connections. 

You can disable the creation of classic build pipelines and classic release pipelines independently. When you disable both, no classic build pipeline, classic release pipeline, task groups, and deployment groups can be created using either the user interface or the REST API.

You can disable creation of classic pipelines by turning on two toggles at either organization level or project level. To turn them on, navigate to your *Organization / Project settings*, then under the *Pipelines* section choose *Settings*. In the *General* section, toggle on *Disable creation of classic build pipelines* and *Disable creation of classic release pipelines*.

When you turn them on at organization level, it is on for all projects in that organization. If you leave them off, you can choose for which projects you wish to turn them on.

:::moniker-end

## Next steps

After you plan your security approach, consider how your [repositories](repos.md) provide protection.
