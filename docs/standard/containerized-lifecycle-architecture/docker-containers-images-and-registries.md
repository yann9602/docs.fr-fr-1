---
title: Registres, des images et des conteneurs docker
description: Cycle de vie Application en conteneur Docker avec la plate-forme Microsoft et les outils
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: b115b25d8ae335aafbe41bac0d694170be7e3c49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="docker-containers-images-and-registries"></a>Registres, des images et des conteneurs docker

Lorsque vous utilisez Docker, vous créez une application ou le service et le package il et ses dépendances dans une image de conteneur. Une image est une représentation statique de l’application ou service de configuration et ses dépendances.

Pour exécuter l’application ou le service, l’image de l’application est instancié pour créer un conteneur, qui est exécuté sur l’hôte Docker. Les conteneurs sont initialement testées dans un environnement de développement ou un PC.

Stocker des images dans un Registre, qui agit comme une bibliothèque d’images. Vous avez besoin d’un Registre lors du déploiement vers orchestrators de production. Docker conserve un registre public via [Hub d’ancrage](https://hub.docker.com/); autres éditeurs proposent des registres pour les différentes collections d’images. Également, les entreprises peuvent avoir un Registre privé local pour leurs propres images Docker.

Figure 1-4 indique comment les images et les registres dans Docker se rapportent à d’autres composants. Il montre également les offres de Registre plusieurs provenant de fournisseurs.

![](./media/image4.png)

Classification de la figure 1-4 : de Docker termes et concepts

En plaçant des images dans un Registre, vous pouvez stocker les bits d’application statique et immuable, y compris toutes leurs dépendances, au niveau d’une infrastructure. Vous pouvez version puis et déployer des images dans plusieurs environnements et donc fournissent une unité de déploiement cohérent.

Les registres de l’image privée, hébergé localement ou dans le cloud, sont recommandés pour les situations suivantes :

-   Vos images ne doivent pas être partagés publiquement en raison de la confidentialité.

-   Vous souhaitez avoir une latence réseau minimum entre vos images et votre environnement de déploiement choisi. Par exemple, si votre environnement de production est Azure, vous souhaiterez probablement stocker vos images dans le Registre de conteneur Azure afin que la latence du réseau sera minime. De la même façon, si votre environnement de production sur site, vous souhaiterez ont un local Docker Trusted Registre disponibles dans le même réseau local.

>[!div class="step-by-step"]
[Précédente] (docker-terminology.md) [suivant] (Docker-application-du cycle de vie/index.md)
