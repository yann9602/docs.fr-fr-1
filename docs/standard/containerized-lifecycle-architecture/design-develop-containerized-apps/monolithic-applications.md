---
title: Applications monolithiques
description: Cycle de vie Application en conteneur Docker avec la plate-forme Microsoft et les outils
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b4b61198129c584909d1345b64dc52feeee7b58e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="monolithic-applications"></a>Applications monolithiques

Dans ce scénario, vous générez une application web unique et monolithique ou le service et déployer en tant que conteneur. Dans l’application, la structure ne peut pas être monolithique ; Il peut comprendre plusieurs bibliothèques, composants ou même des couches (couche application, couche de domaine, couche d’accès aux données, etc.). En externe, il s’agit d’un seul conteneur, comme un processus unique, seule application web ou service unique.

Pour gérer ce modèle, vous déployez un conteneur unique pour représenter l’application. À l’échelle, ajoutez simplement quelques copies plus avec un équilibrage de charge à l’avant. La simplicité provient de la gestion d’un déploiement unique dans un conteneur unique ou d’un ordinateur virtuel (VM).

Suite de l’entité de sécurité qu’un conteneur fait une chose uniquement et qu’il le fait dans un processus, le modèle monolithique est en conflit. Vous pouvez inclure plusieurs composants/bibliothèques ou couches internes dans chaque conteneur, comme illustré dans la Figure 4-1.

![](./media/image1.png)

Figure 4-1 : exemple d’architecture d’application monolithique

L’inconvénient de cette approche est fournie si ou lorsque l’application se développe, nécessitant une mise à l’échelle. Si la mise à l’échelle de l’application entière, il n’est pas réellement un problème. Toutefois, dans la plupart des cas, certaines parties de l’application sont les points d’étranglement qui nécessitent la mise à l’échelle, tandis que les autres composants sont utilisés moins.

À l’aide de l’exemple classique de commerce électronique, cela signifie probablement qu’avez besoin est à l’échelle le composant d’informations de produit. De nombreux clients plus parcourir les produits que les acheter. Davantage de clients utilisent leur panier d’achat que d’utiliser le pipeline de paiement. Les clients moins ajouter des commentaires ou afficher leur historique d’achat. Et vous avez probablement que quelques employés, dans une région unique, qui ont besoin de gérer le contenu et les campagnes marketing. Par la mise à l’échelle de la conception monolithique, tout le code est déployé plusieurs fois.

En plus de la « montée en puissance-tous les éléments « nécessitent des modifications à un seul composant problème, le nouveau test complet de l’ensemble de l’application ainsi que d’un redéploiement complet de toutes les instances.

L’approche monolithique est courant, et développent avec cette méthode architecturale de nombreuses organisations. Nombreux Profitez bon nombre insuffisant de résultats, alors que d’autres limites de rencontrer. Nombreux conçues leurs applications dans ce modèle, car l’infrastructure et les outils ont été trop difficiles à générer SOA, et il n’a pas été voit la nécessité, jusqu'à ce que l’application a fait l’objet.

Du point de vue de l’infrastructure, chaque serveur peut exécuter des applications dans le même hôte et ont un taux acceptable d’efficacité dans votre utilisation des ressources, comme indiqué dans la Figure 4-2.

![](./media/image2.png)

Figure 4-2 : un ordinateur hôte exécutant plusieurs applications/conteneurs

Vous pouvez déployer des applications monolithiques dans Azure à l’aide de machines virtuelles dédiées pour chaque instance. À l’aide de [jeux de mise à l’échelle de machine virtuelle Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), vous pouvez adapter facilement les machines virtuelles. [Services d’application Azure](https://azure.microsoft.com/en-us/services/app-service/) peuvent exécuter des applications monolithiques et gérer facilement des instances sans avoir à gérer les machines virtuelles. Depuis 2016, les Services d’application Azure peut exécute des instances uniques de Docker, en matière de conteneurs, ce qui simplifie le déploiement. Et, à l’aide de Docker, vous pouvez déployer une seule machine virtuelle comme un hôte Docker et exécuter plusieurs instances. À l’aide de l’équilibrage de Azure, comme illustré dans la Figure 4-3, vous pouvez gérer la mise à l’échelle.

![](./media/image3.png)

Figure 4-3 : plusieurs hôtes montée en une seule application applications/conteneurs Docker

Vous pouvez gérer le déploiement sur les différents hôtes via les techniques de déploiement traditionnelles. Vous pouvez gérer les hôtes Docker à l’aide des commandes telles que `docker run` manuellement, à l’aide d’automation, tels que les pipelines de livraison continue (CD), ce qui nous expliquons plus loin dans ce livre électronique.

## <a name="monolithic-application-deployed-as-a-container"></a>Application monolithique déployée comme un conteneur

Il existe des avantages à utiliser des conteneurs pour gérer les déploiements monolithiques. Mise à l’échelle les instances de conteneurs est beaucoup plus rapide et plus facile que le déploiement de machines virtuelles supplémentaires. Bien que les groupes de VM identiques sont une fonctionnalité intéressante à l’échelle de machines virtuelles, qui sont requis pour héberger vos conteneurs Docker, ils de temps configuré. Lors du déploiement en tant qu’instances de l’application, la configuration de l’application est gérée dans le cadre de la machine virtuelle.

Déploiement des mises à jour comme images Docker est beaucoup plus rapide et efficace du réseau. Les instances Vn peuvent être configurés sur les mêmes hôtes que vos instances Vn-1, en éliminant les coûts supplémentaires résultant des machines virtuelles supplémentaires. Les images docker démarrent généralement en secondes, ce qui accélère les déploiements. Destruction d’une instance de Docker est aussi simple que l’appel du `docker stop` commande, généralement à la fin dans moins d’une seconde.

Étant donné que les conteneurs sont par nature immuables, par conception, vous devez jamais à vous soucier des machines virtuelles endommagés, car vous avez oublié par un script de mise à jour pour prendre en compte une configuration spécifique ou d’un fichier restant sur le disque.

Bien que les applications monolithiques peuvent tirer parti de Docker, nous allons abordant uniquement les conseils des avantages. Les avantages de plus grandes de la gestion des conteneurs proviennent de déploiement avec orchestrators de conteneur qui gèrent les différentes instances et cycle de vie de chaque instance de conteneur. Interrompre l’application monolithique en sous-systèmes qui peuvent être mis à l’échelle, développés et déployés de manière individuelle est votre point d’entrée dans le domaine de microservices.

## <a name="publishing-a-single-docker-container-app-to-azure-app-service"></a>Publication d’une seule application de conteneur Docker dans Azure App Service

Soit parce que vous voulez obtenir une validation rapide d’un conteneur déployé sur Azure ou parce que l’application est simplement une application conteneur unique, les Services d’application Azure fournit un excellent moyen de fournir des services de conteneur unique évolutives.

À l’aide du Service d’applications Azure est intuitif et vous pouvez obtenir et exécute rapidement, car elle fournit une excellente Git intégration prendre votre code, générez-le dans Microsoft Visual Studio et déployer directement vers Azure. Mais, traditionnellement (avec aucune Docker), si vous avez besoin d’autres fonctionnalités, les infrastructures ou les dépendances qui ne sont pas pris en charge dans les Services d’application, vous nécessaire d’attendre jusqu'à ce que l’équipe Azure met à jour ces dépendances dans le Service d’applications ou basculé vers d’autres services tels que Service Fabric, Services de cloud computing ou même brut machines virtuelles, pour lequel vous avez davantage de contrôle et pourrez installer un framework ou un composant requis pour votre application.

Désormais, cependant, (annoncé à Microsoft Connect 2016 en novembre 2016) et comme indiqué dans la Figure 4‑4, lors de l’utilisation de Visual Studio 2017, prise en charge du conteneur dans Azure App Service vous donne la possibilité d’inclure tout ce que vous voulez dans votre environnement d’application. Si vous avez ajouté une dépendance à votre application, car vous l’exécutez dans un conteneur, vous obtenez la fonctionnalité d’intégration de ces dépendances dans votre image Dockerfile ou Docker.

![](./media/image4.png)

Figure 4-4 : publication d’un conteneur vers Azure App Service à partir des conteneurs/applications Visual Studio

Figure 4-4 montre également que le flux de publication exécute un push d’une image à un Registre de conteneur, qui peut être le Registre de conteneur Azure (un Registre près à vos déploiements dans Azure et sécurisé par des comptes et groupes Azure Active Directory) ou tout autre registre Docker comme les registres de Hub d’ancrage ou localement.


>[!div class="step-by-step"]
[Précédente] (commun-conteneur-design-principles.md) [suivant] (state-and-data-in-docker-applications.md)
