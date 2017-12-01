---
title: Applications monolithiques containerizing
description: Architecture de Microservices .NET pour les Applications .NET en conteneur | Applications monolithiques containerizing
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 11e2c24403b9b61584e424696c844e00e5d34b03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="containerizing-monolithic-applications"></a>Applications monolithiques containerizing

Vous souhaiterez peut-être générer une application web unique, monolithiquement déployé ou le service et le déployer en tant que conteneur. L’application elle-même ne peut pas être monolithique en interne, mais structuré comme plusieurs bibliothèques, composants ou même couches (couche application, couche de domaine, couche d’accès aux données, etc.). En externe, toutefois, il est un conteneur unique, un processus unique, une seule application web ou un service unique.

Pour gérer ce modèle, vous déployez un conteneur unique pour représenter l’application. Pour faire évoluer verticalement, il suffit d’ajouter plus de copies avec un équilibrage de charge à l’avant. La simplicité provient de la gestion d’un déploiement unique dans un seul conteneur ou d’une machine virtuelle.

![](./media/image1.png)

**La figure 4-1**. Exemple de l’architecture d’une application monolithique en conteneur

Vous pouvez inclure plusieurs composants, des bibliothèques ou des couches internes dans chaque conteneur, comme illustré dans la Figure 4-1. Toutefois, ce modèle monolithique peut-être entrer en conflit avec le principe de conteneur « un conteneur effectue une opération et le fait dans un processus », mais peuvent être OK dans certains cas.

L’inconvénient de cette approche devient évident que si l’application évolue, nécessitant une mise à l’échelle. Si l’ensemble de l’application puisse évoluer, il n’est pas réellement un problème. Toutefois, dans la plupart des cas, quelques parties de l’application sont les points d’étranglement que nécessitant une mise à l’échelle, tandis que les autres composants sont moins utilisé.

Par exemple, dans une application de commerce électronique typique, vous probablement besoin de mettre à l’échelle le sous-système d’informations de produit, car de nombreux clients plus parcourir les produits que les acheter. Davantage de clients utilisent leur panier d’achat que d’utiliser le pipeline de paiement. Les clients moins ajouter des commentaires ou afficher leur historique d’achat. Et vous pouvez avoir seulement quelques employés, qui ont besoin pour gérer le contenu et les campagnes marketing. Si vous redimensionnez la conception monolithique, tout le code pour ces différentes tâches est déployé plusieurs fois et à l’échelle le même niveau.

Il existe plusieurs manières de faire évoluer une application, déduplication horizontale, fractionnement des différentes zones de l’application et de partitionnement similaire concepts d’entreprise ou de données. Toutefois, en plus du problème de mise à l’échelle de tous les composants, les modifications apportées à un seul composant nécessitent un nouveau test complet de l’application entière et un redéploiement complet de toutes les instances.

Toutefois, l’approche monolithique est courant, étant donné que le développement de l’application est initialement plus facile que pour les approches de microservices. Par conséquent, de nombreuses organisations développent à l’aide de cette approche architecturale. Alors que certaines organisations ont été bon nombre insuffisant de résultats, d’autres atteignez les limites. De nombreuses organisations conçu leurs applications à l’aide de ce modèle, car les outils et infrastructure rendaient trop difficile pour le service de build orientée services (SOA) des architectures ans, et ils ne voyait pas le besoin, jusqu'à ce que l’application a fait l’objet.

Du point de vue de l’infrastructure, chaque serveur peut exécuter des applications dans le même hôte et ont un taux acceptable de l’efficacité de l’utilisation de ressources, comme indiqué dans la Figure 4-2.

![](./media/image2.png)

**Figure 4-2**. Approche monolithique : héberger plusieurs applications, en cours d’exécution de chaque application en cours d’exécution en tant que conteneur

Les applications monolithiques dans Microsoft Azure peuvent être déployées à l’aide de machines virtuelles dédiées pour chaque instance. En outre, à l’aide de [jeux de mise à l’échelle de machine virtuelle Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), vous pouvez adapter facilement les machines virtuelles. [Azure App Service](https://azure.microsoft.com/services/app-service/) peut également exécuter des applications monolithiques et gérer facilement des instances sans avoir à gérer les machines virtuelles. Depuis 2016, Azure App Services peuvent s’exécuter des instances uniques des conteneurs Docker, ce qui simplifie le déploiement.

Comme un environnement d’assurance qualité ou d’un environnement de production limité, vous pouvez déployer un hôte Docker plusieurs machines virtuelles et équilibrer à l’aide de l’équilibrage de Azure, comme indiqué dans la Figure 4-3. Cela vous permet de gérer mise à l’échelle avec une approche de granularité grossière, étant donné que la totalité de l’application se trouve dans un conteneur unique.

![](./media/image3.png)

**Figure 4-3**. Exemple de mise à l’échelle d’une application conteneur unique de plusieurs ordinateurs hôtes

Déploiement sur les ordinateurs hôtes différents peut être géré avec les techniques de déploiement traditionnelles. Hôtes docker peuvent être gérés avec les commandes telles que `docker run` ou `docker-compose` effectué manuellement ou via l’automatisation, telles que les pipelines de livraison continue (CD).

## <a name="deploying-a-monolithic-application-as-a-container"></a>Déploiement d’une application monolithique en tant que conteneur

Il existe des avantages à utiliser des conteneurs pour gérer les déploiements d’applications monolithique. Mise à l’échelle les instances du conteneur est beaucoup plus rapide et plus facile que le déploiement de machines virtuelles supplémentaires. Même si vous utilisez des jeux de mise à l’échelle de machine virtuelle, machines virtuelles de temps pour démarrer. Lors du déploiement en tant qu’instances d’application traditionnel au lieu de conteneurs, la configuration de l’application est gérée dans le cadre de la machine virtuelle, ce qui n’est pas idéal.

Déploiement des mises à jour comme images Docker est beaucoup plus rapide et efficace du réseau. Les images docker démarrent généralement en secondes, ce qui accélère les déploiements. Destruction d’une instance d’image Docker est aussi simple que l’émission d’un `docker stop` , puis se termine généralement en moins d’une seconde.

Étant donné que les conteneurs sont immuables par sa conception, vous devez jamais à vous soucier des machines virtuelles endommagés. En revanche, les scripts de mise à jour pour une machine virtuelle peuvent oubliez pour prendre en compte une configuration spécifique ou d’un fichier restant sur le disque.

Alors que les applications monolithiques peuvent tirer parti de Docker, nous allons toucher uniquement sur les avantages. Autres avantages de la gestion des conteneurs proviennent de déploiement avec orchestrators de conteneur, qui gèrent les différentes instances et cycle de vie de chaque instance de conteneur. Interrompre l’application monolithique en sous-systèmes qui peuvent être mis à l’échelle, développés et déployés de manière individuelle est votre point d’entrée dans le domaine de microservices.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Publication d’une application simple basée sur conteneur vers Azure App Service

Si vous souhaitez obtenir la validation d’un conteneur déployé sur Azure, ou lorsqu’une application est simplement une application conteneur unique, du Service d’applications Azure fournit un excellent moyen de fournir des services évolutifs basées sur le conteneur unique. À l’aide du Service d’applications Azure est simple. Il fournit une parfaite intégration avec Git pour faciliter la déconnecter votre code, générez-le dans Visual Studio et déployez-le directement sur Azure.

![](./media/image4.png)

**Figure 4-4**. Publication d’une application conteneur unique au Service d’application Azure depuis Visual Studio

Sans Docker, si vous avez besoin d’autres fonctionnalités, les infrastructures ou les dépendances qui ne sont pas pris en charge dans Azure App Service, vous deviez patienter jusqu'à ce que l’équipe Azure mis à jour ces dépendances dans le Service d’applications. Ou bien, vous deviez basculer vers d’autres services tels que Azure Service Fabric, les Services de cloud computing Azure ou même les machines virtuelles, où vous avez davantage de contrôle et que vous pouviez installer un framework ou un composant requis pour votre application.

Prise en charge de conteneur dans Visual Studio 2017 vous donne la possibilité d’inclure tout ce que vous voulez dans votre environnement d’application, comme indiqué dans la Figure 4-4. Étant donné que vous l’exécutez dans un conteneur, si vous ajoutez une dépendance à votre application, vous pouvez inclure la dépendance dans votre image Dockerfile ou Docker.

Comme illustré dans la Figure 4-4, le flux de publication exécute un push d’une image à un Registre de conteneur. Cela peut être le Registre de conteneur Azure (un Registre fermer à vos déploiements dans Azure et sécurisé par des comptes et groupes Azure Active Directory), ou tout autre registre Docker, tels que Docker Hub ou un Registre local.


>[!div class="step-by-step"]
[Précédente] (index.md) [suivant] (docker-application-état-data.md)
