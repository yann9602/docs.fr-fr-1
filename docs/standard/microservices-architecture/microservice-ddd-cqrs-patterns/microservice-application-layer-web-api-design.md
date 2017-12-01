---
title: "Conception de la couche d’application microservice et l’API Web"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Conception de la couche d’application microservice et l’API Web"
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7509b470a30005dd48fa88eefa91f7ed241e4e09
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a>Conception de la couche d’application microservice et l’API Web

## <a name="using-solid-principles-and-dependency-injection"></a>À l’aide de solides principes et Injection de dépendance

Principes de solides sont critiques techniques à utiliser dans des applications modernes et critiques, tels que le développement d’un microservice avec des modèles de DDD. SOLIDE est l’acronyme groupes cinq des principes fondamentaux :

-   Principe de responsabilité unique

-   Principe d’ouverture/fermeture

-   Principe de substitution de Liskov

-   Principe d’inversion de la segmentation

-   Principe d’Inversion de dépendance

SOLIDE est plus sur la façon dont vous concevez votre application ou les couches interne de microservice et découplage des dépendances entre eux. Il n’est pas lié au domaine, mais à la conception technique de l’application. Le principe final, le principe d’Inversion de dépendance (DI), vous permet de découpler la couche d’infrastructure du reste des couches, ce qui permet une implémentation de mieux découplée des couches DDD.

DI est une façon d’implémenter le principe d’Inversion de dépendance. Il est une technique de couplage lâche entre les objets et leurs dépendances. Au lieu d’instancier directement des collaborateurs, ou à l’aide de références statiques, les objets dont une classe a besoin pour effectuer ses actions sont fournies à (ou « injecter ») la classe. En règle générale, les classes déclarer leurs dépendances via leur constructeur, ce qui leur permet de respecter le principe de dépendances explicites. DI est généralement basée sur des conteneurs d’Inversion de contrôle (IoC) spécifiques. ASP.NET Core fournit un simple conteneur inversion de contrôle intégré, mais vous pouvez également utiliser votre conteneur IoC favoris, tels que Autofac ou Ninject.

En suivant les principes solides, vos classes tendent naturellement être petit, bien factorisée et facilement testées. Mais comment vous saurez si trop de dépendances sont en cours injectées dans vos classes ? Si vous utilisez DI via le constructeur, il sera facile de détecter qu’en examinant le nombre de paramètres pour votre constructeur. S’il y a trop de dépendances, il s’agit généralement d’un signe (un [code odeur](http://deviq.com/code-smells/)) que votre classe essaie de faire de façon trop importante et probablement viole le principe de responsabilité unique.

Il faudrait un autre guide pour couvrir solide en détail. Par conséquent, ce guide vous oblige à ont des connaissances minimales des rubriques suivantes.

#### <a name="additional-resources"></a>Ressources supplémentaires

-   **SOLIDE : Principes de programmation orientée objet fondamentaux**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)

-   **Inversion des conteneurs de contrôle et le modèle d’Injection de dépendances**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)

-   **Steve Smith. Nouveaux est de type Glue**
    [*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)


>[!div class="step-by-step"]
[Précédente] (nosql-base de données-persistance-infrastructure.md) [suivant] (microservice-application-layer-implementation-web-api.md)
