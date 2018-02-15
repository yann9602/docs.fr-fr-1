---
title: "Technologies Microsoft dans les applications cloud devops prêt"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Technologies Microsoft dans les applications de DevOps prête pour le Cloud"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3212bf1e938b789d68ca76dd06ce53a2788244b6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="microsoft-technologies-in-cloud-devops-ready-applications"></a>Technologies Microsoft dans les applications cloud devops prêt

La liste suivante décrit les outils, les technologies et les solutions qui sont reconnues comme des spécifications pour les applications de DevOps prête pour le Cloud. Vous pouvez adopter les applications Cloud DevOps prêt progressivement, ou de manière sélective en fonction de vos priorités.

-   **Infrastructure de nuage**: l’infrastructure qui fournit la plateforme de calcul, le système d’exploitation, le réseau et le stockage. Microsoft Azure est positionné à ce niveau.

-   **Runtime**: cette couche fournit l’environnement pour exécuter l’application. Si vous utilisez des conteneurs, cette couche est généralement basée sur [moteur Docker](https://docs.docker.com/engine/), en cours d’exécution sur les hôtes Linux ou sur les hôtes Windows. ([Les conteneurs Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) sont pris en charge à partir de Windows Server 2016. Les conteneurs Windows est le meilleur choix pour les applications .NET Framework existantes qui s’exécutent sur Windows.)

-   **Gérés cloud**: lorsque vous choisissez une option de cloud géré, vous pouvez éviter les coûts et la complexité de la gestion et les correctifs de système d’exploitation sous-jacent infrastructure, les machines virtuelles, de prise en charge et mise en réseau de configuration. Si vous choisissez de migrer à l’aide de IaaS, vous êtes responsable de toutes ces tâches, ainsi que pour les coûts associés. Une option cloud géré, vous permet de gérer uniquement les applications et les services que vous développez. Le fournisseur de services cloud gère habituellement tout le reste. Exemples de services de cloud géré dans Azure [base de données SQL Azure](https://azure.microsoft.com/services/sql-database), [Cache Redis Azure](https://azure.microsoft.com/services/cache/), [base de données Azure Cosmos](https://azure.microsoft.com/services/cosmos-db/), [Azure Storage](https://azure.microsoft.com/services/storage/), [Base de données azure pour MySQL](https://azure.microsoft.com/services/mysql/), [base de données Azure pour PostgreSQL](https://azure.microsoft.com/services/postgresql/), [Azure Active Directory](https://azure.microsoft.com/services/active-directory/)et gérés comme les services de calcul [l’échelle de machine virtuelle définit](https://azure.microsoft.com/services/virtual-machine-scale-sets/), [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/), [Azure App Service](https://azure.microsoft.com/services/app-service/), et [Service de conteneur Azure](https://azure.microsoft.com/services/container-service/).

-   **Développement d’applications**: vous pouvez choisir de nombreux langages lorsque vous générez des applications qui s’exécutent dans des conteneurs. Dans ce guide, nous concentrer sur [.NET](https://www.microsoft.com/net), mais vous pouvez développer des applications basées sur le conteneur à l’aide d’autres langages, tels que de Node.js, Python, ressort/Java ou GoLang.

-   **Télémétrie, journalisation et d’audit, d’analyse**: la possibilité pour les applications d’analyse et d’audit et les conteneurs qui sont en cours d’exécution dans le cloud est essentielle pour n’importe quelle application DevOps prête pour le Cloud. [Azure Application Insights](https://azure.microsoft.com/services/application-insights/) et [Microsoft Operations Management Suite](https://www.microsoft.com/cloud-platform/operations-management-suite) sont les principaux outils de Microsoft qui fournissent la surveillance et l’audit pour les applications de DevOps prête pour le Cloud.

-   **Approvisionnement**: outils d’automatisation vous aider à configurer l’infrastructure et de déployer une application dans plusieurs environnements (production, test, intermédiaire). Vous pouvez utiliser des outils comme Chef et Puppet pour gérer la configuration d’une application et l’environnement. Cette couche permettre également être implémentée à l’aide des approches plus simples et plus directes. Par exemple, vous pouvez déployer directement à l’aide d’Azure interface de ligne de commande (CLI d’Azure) pour les outils et ensuite utiliser le déploiement continu et libérer des pipelines de gestion dans [Visual Studio Team Services](https://www.visualstudio.com/team-services/).

-   **Cycle de vie application**: [Visual Studio Team Services](https://www.visualstudio.com/team-services/) et d’autres outils, tels que Jenkins, sont build Automation (serveurs) qui vous aident à implémentent l’élément de configuration/CD pipelines, y compris la gestion de version.

Les sections suivantes de ce chapitre et les procédures associées, traitent spécifiquement de plus d’informations sur la couche d’exécution (les conteneurs Windows). Le guide décrit les méthodes que vous pouvez déployer des machines virtuelles de conteneurs Windows sur Windows Server 2016 (et versions ultérieures). Elle traite également des couches orchestrator plus avancées, telles que Azure Service Fabric, Kubernetes et Service de conteneur Azure. Configuration des couches d’orchestrator est une condition fondamentale pour rénovation .NET Framework (Windows) les applications existantes en tant qu’applications de DevOps prête pour le Cloud.

## <a name="monolithic-applications-can-be-cloud-devops-ready"></a>Applications monolithiques *pouvez* être DevOps prête pour le Cloud

Il est important de souligner que les applications (applications qui ne sont pas basées sur microservices) monolithique *pouvez* être DevOps prête pour le Cloud des applications. Vous pouvez générer et monolithiques applications qui tirent parti du cloud computing de modèle à l’aide d’une combinaison des conteneurs, livraison continue et DevOps de fonctionner. Si une application monolithique existante ne répond à vos objectifs, vous pouvez il moderniser et rendre DevOps prête pour le Cloud.

De même, si les applications monolithiques peuvent être des applications de DevOps prête pour le Cloud, les architectures autres et plus complexes telles que des applications multicouches également peuvent être modernisés en tant qu’applications de DevOps prête pour le Cloud.

>[!div class="step-by-step"]
[Précédent](reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications.md)
[Suivant](what-about-cloud-optimized-applications.md)
