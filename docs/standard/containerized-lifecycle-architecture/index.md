---
title: "Présentation des conteneurs et de Docker"
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 4e79c4658492516e33efc0b33408e3d4220640f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="introduction-to-containers-and-docker"></a>Présentation des conteneurs et de Docker

La mise en conteneur est une approche de développement de logiciels qui consiste à empaqueter une application ou un service, ses dépendances et sa configuration (extraits sous forme de fichiers manifeste de déploiement) sous forme d’image de conteneur. Vous pouvez ensuite tester l’application en conteneur en tant qu’unité et la déployer sous forme d’instance d’image de conteneur sur le système d’exploitation hôte.

De la même manière que l’industrie du transport utilise des conteneurs normalisés pour transporter des marchandises par bateau, train ou camion, et ce indépendamment de la nature de la cargaison, les conteneurs logiciels agissent comme une unité logicielle standard qui peut contenir du code et des dépendances différents. Le fait de placer des logiciels dans des conteneurs permet aux développeurs et informaticiens de déployer ces conteneurs dans les environnements avec peu ou pas de modifications.

Les conteneurs isolent également les applications les unes des autres sur un système d’exploitation partagé. Les applications en conteneur s’exécutent sur un hôte de conteneurs qui à son tour s’exécute sur le système d’exploitation (Linux ou Windows). Les conteneurs ont donc un encombrement bien moindre que les images de machine virtuelle.

Chaque conteneur peut exécuter un service ou une application web dans son intégralité, comme l’illustre la figure 1-1.

![](./media/image1.png)

Figure 1-1 : Plusieurs conteneurs s’exécutant sur un hôte de conteneurs

Dans cet exemple, l’hôte Docker est un hôte de conteneurs, et App1, App2, Svc 1 et Svc 2 sont des applications ou des services en conteneur.

L’autre avantage qui dérive de la mise en conteneur est la scalabilité. Vous pouvez rapidement monter en charge en créant des conteneurs pour des tâches à court terme. Du point de vue de l’application, *instancier une image* (c.-à-d., créer un conteneur) revient à instancier un processus comme un service ou une application web. Cependant, dans un souci de fiabilité, quand il s’agit d’exécuter plusieurs instances d’une même image sur plusieurs serveurs hôtes, il est en principe préférable que chaque conteneur (instance d’image) s’exécute sur un serveur hôte différent ou sur une machine virtuelle dans différents domaines d’erreur.

Pour résumer, les conteneurs offrent les avantages de l’isolation, de la portabilité, de l’agilité, de l’extensibilité et du contrôle dans l’ensemble du flux de travail du cycle de vie de l’application. L’avantage le plus important est l’isolation entre le développement et les opérations.


>[!div class="step-by-step"]
[Suivant] (what-is-docker.md)
