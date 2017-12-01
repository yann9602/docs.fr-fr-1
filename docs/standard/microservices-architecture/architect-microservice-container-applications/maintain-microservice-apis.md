---
title: "Création, en constante évolution et le contrôle de version microservice API et des contrats"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Création, en constante évolution et le contrôle de version microservice API et des contrats"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 433711c3479eafd52bf9f5d53faf8e5707c6c624
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Création, en constante évolution et le contrôle de version microservice API et des contrats

Une API de microservice est un contrat entre le service et ses clients. Vous ne pourrez pas un microservice évoluer indépendamment les uns uniquement si vous n’arrêtez pas son contrat d’API, c’est pourquoi le contrat est si important. Si vous modifiez le contrat, il aura un impact sur vos applications clientes ou votre passerelle API.

La nature de la définition de l’API dépend de protocole que vous utilisez. Par exemple, si vous utilisez la messagerie (comme [AMQP](https://www.amqp.org/)), l’API se compose des types de messages. Si vous utilisez HTTP et des services RESTful, l’API comprend les URL et les formats JSON de demande et de réponse.

Toutefois, même si vous êtes réfléchie sur votre contrat initial, une API du service vous devrez modifier au fil du temps. Lorsque cela se produit, et en particulier si votre API est une API publique utilisée par plusieurs applications clientes, vous ne pouvez pas généralement forcer tous les clients à mettre à niveau vers votre nouveau contrat d’API. Vous devez généralement déployer de nouvelles versions d’un service d’une manière anciennes et nouvelles versions d’un contrat de service sont exécutent simultanément. Par conséquent, il est important de disposer d’une stratégie de contrôle de version de votre service.

Lorsque les modifications de l’API sont petites, comme si vous ajoutez des attributs ou des paramètres à votre API, les clients qui utilisent une API antérieure doivent basculer et travailler avec la nouvelle version du service. Vous pourrez fournir des valeurs par défaut pour tous les attributs manquants sont requis, et les clients peuvent être en mesure d’ignorer les attributs de la réponse en trop.

Toutefois, vous devez parfois apporter des modifications majeures et incompatibles à une API de service. Étant donné que vous n’êtes peut-être pas en mesure de forcer les applications clientes ou les services de mise à niveau immédiatement vers la nouvelle version, un service doit prendre en charge des versions antérieures de l’API pour une période donnée. Si vous utilisez un mécanisme basé sur HTTP, tels que REST, une approche consiste à incorporer le numéro de version d’API dans l’URL ou dans un en-tête HTTP. Vous pouvez alors décider entre les deux versions du service simultanément dans la même instance de service de mise en œuvre ou le déploiement de différentes instances que chacun gérant une version de l’API. Une bonne approche pour cela est la [modèle de médiateur](https://en.wikipedia.org/wiki/Mediator_pattern) (par exemple, [MediatR bibliothèque](https://github.com/jbogard/MediatR)) pour dissocier les versions de mise en œuvre différents gestionnaires indépendant.

Enfin, si vous utilisez une architecture REST, [hypermédia](https://www.infoq.com/articles/mark-baker-hypermedia) est la meilleure solution pour le contrôle de version de vos services et de laisser des API évolutive.

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Scott Hanselman. Contrôle de version de l’API Web RESTful principale ASP.NET facilité**
    <http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

-   **Le contrôle de version une API web RESTful**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Roy fielding d’a. Le contrôle de version, hypermédia et reste**
    <https://www.infoq.com/articles/roy-fielding-on-versioning>


>[!div class="step-by-step"]
[Précédente] (asynchrone-message-base-communication.md) [suivant] (microservices-adressabilité-service-registry.md)
