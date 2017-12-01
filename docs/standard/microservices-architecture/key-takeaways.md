---
title: "points clés"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | points clés"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b557d0b641bfe95c025cadb13f82c3f8927f4bc8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="key-takeaways"></a>Points clés

En tant qu’un résumé et des points, voici les conclusions plus importantes à partir de ce guide.

**Avantages de l’utilisation de conteneurs.** Solutions basées sur le conteneur offrent l’avantage important de réduction des coûts, car les conteneurs sont une solution aux problèmes de déploiement en raison du manque de dépendances dans les environnements de production. Conteneurs améliorer considérablement les opérations de production et de DevOps.

**Conteneurs sera très répandues.** Conteneurs docker deviennent la norme du secteur de conteneur, pris en charge par les fournisseurs plus significatifs dans les écosystèmes Windows et Linux. Cela inclut Microsoft, Amazon AWS, Google et IBM. Dans un futur proche, Docker sera probablement très répandue dans les centres de données à la fois locaux et cloud.

**Conteneurs en tant qu’unité de déploiement.** Un conteneur Docker devient l’unité de déploiement pour toute application basée sur le serveur ou le service standard.

**Microservices.** L’architecture de microservices devient la meilleure approche pour les applications critiques en distribuée et volumineuse ou complexes selon plusieurs sous-systèmes indépendants sous la forme de services autonomes. Dans une architecture microservice, l’application est générée comme une collection de services qui peuvent être développés, testés, version, déployé et à l’échelle de manière indépendante ; Cela peut inclure une base de données autonome connexe.

**Conception domaine et SOA.** Les modèles d’architecture microservices dérivent de l’architecture orientée services (SOA) et de conception domaine (DDD). Lorsque vous concevez et développez des microservices pour les environnements à l’évolution des règles d’entreprise mise en forme d’un domaine particulier, il est important de prendre en compte DDD approches et les modèles.

**Microservices défis.** Microservices offrent de nombreuses fonctionnalités puissantes comme indépendant de déploiement des limites du sous-système fort et diversité de technologie. Toutefois, ils déclenchent également plusieurs nouveaux défis associés au développement d’applications distribuées, telles que fragmenté et modèles de données indépendant, communication résiliente entre microservices et la complexité opérationnelle qui résulte de la cohérence éventuelle agrégation des informations de journalisation et d’analyse à partir de plusieurs microservices. Ces aspects présentent un niveau supérieur de complexité à une application monolithique traditionnelle. Par conséquent, des scénarios spécifiques conviennent pour les applications microservice. Ceux-ci incluent des applications volumineuses et complexes avec plusieurs sous-systèmes en constante évolution ; dans ces cas, il est investir dans une architecture de logiciel plus complexe, car elle fournit à long terme une meilleure souplesse et une maintenance de l’application.

**Conteneurs pour n’importe quelle application.** Conteneurs sont pratiques pour microservices, mais ne sont pas exclusifs pour eux. Conteneurs peuvent également servir aux applications monolithiques, y compris les applications héritées basé sur le .NET Framework traditionnelles et modernisé via les conteneurs Windows. Les avantages de l’utilisation de Docker, telles que la résolution de nombreux problèmes de déploiement de production et en fournissant des environnements de développement et de Test de pointe, s’appliquent à différents types d’applications.

**CLI par rapport à l’IDE.** Avec les outils de Microsoft, vous pouvez développer des applications .NET en conteneur à l’aide de votre approche par défaut. Vous pouvez développer avec une interface CLI et un environnement basé sur l’éditeur à l’aide de l’interface CLI de Docker et d’un Code de Visual Studio. Ou vous pouvez utiliser une approche axée sur l’IDE avec Visual Studio et ses fonctionnalités uniques pour Docker, telles que comme étant en mesure de déboguer des applications conteneur multi.

**Applications résilientes du cloud.** Dans les systèmes basés sur le cloud et de systèmes distribués, en général, il est toujours le risque de défaillance partielle. Étant donné que les clients et services sont des processus distincts (conteneurs), un service n’est peut-être pas en mesure de répondre à une demande du client à un moment opportun. Par exemple, un service peut être vers le bas en raison d’une défaillance partielle ou de maintenance ; le service peut être surchargé et répondre extrêmement lent à la demande ; ou bien, il peut simplement être accessible pour une courte période en raison de problèmes de réseau. Par conséquent, une application basée sur le cloud doit adopter ces défaillances et mettre en œuvre pour répondre à ces défaillances une stratégie. Ces stratégies peuvent inclure des stratégies de nouvelle tentative (renvoi des messages ou une nouvelle tentative de demandes) et implémentation des modèles de disjoncteur afin d’éviter la valeur exponentielle de charge des requêtes répétées. En fait, les applications cloud doivent avoir des mécanismes résilients — personnalisé celles, ou ceux basés sur une infrastructure cloud, tels que les infrastructures de haut niveau à partir d’orchestrators ou le bus de service.

**Sécurité.** Notre monde moderne de conteneurs et microservices peut exposer de nouvelles vulnérabilités. Sécurité de l’application de base est basée sur l’authentification et d’autorisation ; Il existe plusieurs façons pour les implémenter. Toutefois, la sécurité de conteneur inclut les composants clés supplémentaires qui génèrent les applications intrinsèquement plus sûres. Un élément essentiel de la création d’applications plus sûres rencontre un moyen sécurisé de communiquer avec d’autres applications et les systèmes, quelque chose requiert souvent des informations d’identification, les jetons, les mots de passe et autres types d’informations confidentielles, généralement appelées secrets de l’application. Une solution sécurisée doit suivre les meilleures pratiques de sécurité, telles que le chiffrement des clés secrètes en cours de transit ; chiffrement des clés secrètes au repos ; et empêche que les secrets involontairement une fuite lorsque consommé par l’application finale. Ces clés secrètes doivent être stockées et protégées quelque part. Pour améliorer la sécurité, vous pouvez tirer parti de l’infrastructure de votre orchestrator choisi, ou de l’infrastructure de cloud comme Azure Key Vault et les méthodes qu’il fournit pour le code d’application pour l’utiliser.

**Orchestrators.** Basé sur le conteneur orchestrators telles que celles fournies dans le Service de conteneur Azure (Kubernetes Mesos DC/OS et Docker Swarm) et Azure Service Fabric sont indispensables pour n’importe quelle application prête à la production microservice et pour n’importe quel conteneur multiples application avec une complexité significative, les besoins de l’évolutivité et constante évolution. Ce guide propose orchestrators et leur rôle dans les solutions basées sur le conteneur et microservice. Si les besoins de votre application vous déplacez vers des applications en conteneur complexes, il sera utile rechercher des ressources supplémentaires pour en savoir plus sur orchestrators

>[!div class="step-by-step"]
[Précédente] (secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)
