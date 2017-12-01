---
title: "État et les données dans les applications de Docker"
description: Cycle de vie Application en conteneur Docker avec la plate-forme Microsoft et les outils
keywords: Docker, microservices, ASP.NET, conteneur
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 61cd88ca8dd7e51759111d6a9357c008458ee41a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="state-and-data-in-docker-applications"></a>État et les données dans les applications de Docker

Une primitive de conteneurs est que l’immuabilité. Quand elle est comparée à une machine virtuelle, les conteneurs ne disparaissent comme une occurrence courante. Une machine virtuelle peut échouer dans différentes formes à partir des processus, surcharge de l’UC ou un disque complet ou ayant échoué. Encore, nous pensons que la machine virtuelle soit disponible et de disques RAID sont courants pour vous assurer de défaillances de disque conserver les données.

Toutefois, les conteneurs sont supposées être des instances de processus. Un processus ne conservent l’état durable. Même si un conteneur peut écrire dans un stockage local, en supposant que cette instance sera autour indéfiniment serait équivalente à en supposant qu'une copie unique de la mémoire sera durable. Vous devez supposer que les conteneurs, tels que des processus, sont dupliqués, arrêté, ou lorsque gérés par un orchestrateur de conteneur, ils peuvent être déplacés.

Docker utilise une fonctionnalité appelée un *superposition de système de fichiers* pour implémenter un processus de copie sur écriture qui les stocke des informations mises à jour au système de fichiers racine d’un conteneur, par rapport à l’image d’origine sur lequel il est basé. Ces modifications sont perdues si le conteneur est supprimé par la suite à partir du système. Un conteneur, par conséquent, n’a pas le stockage persistant par défaut. Bien qu’il soit possible d’enregistrer l’état d’un conteneur, vous concevez un système de contourner ce problème serait en conflit avec le principe de l’architecture de conteneur.

Pour gérer les données persistantes dans les applications de Docker, il existe des solutions courantes :

-   [**Volumes de données**](https://docs.docker.com/engine/tutorials/dockervolumes/) ces monter à l’hôte, comme indiqué uniquement.

-   [**Conteneurs de volumes de données**](https://docs.docker.com/engine/tutorials/dockervolumes/#/creating-and-mounting-a-data-volume-container) ils fournissent un stockage partagé entre les conteneurs, à l’aide d’un conteneur externe que vous pouvez parcourir.

-   [**Plug-ins de volume**](https://docs.docker.com/engine/tutorials/dockervolumes/#/mount-a-shared-storage-volume-as-a-data-volume) ces monter des volumes à distance, en fournissant la persistance à long terme.

-   **Sources de données distantes** exemples incluent des bases de données SQL et non-SQL ou de mettre en cache des services tels que Redis.

-   [**Le stockage Azure**](https://docs.microsoft.com/azure/storage/) ainsi un stockage de service (PaaS), qui offre le meilleur de conteneurs de persistance à long terme comme plateforme distribuable de géo-réplication.

Volumes de données sont désignés spécialement de répertoires dans un ou plusieurs conteneurs qui ignorent la [système de fichiers Union](https://docs.docker.com/v1.8/reference/glossary#union-file-system). Volumes de données sont conçus pour mettre à jour les données, indépendamment du cycle de vie du conteneur. Docker donc jamais supprime automatiquement les volumes lorsque vous supprimez un conteneur, ni s’il les volumes « collecter garbage » qui ne sont plus référencés par un conteneur. Le système d’exploitation hôte peuvent parcourir et modifier les données dans n’importe quel volume de librement, qui est simplement une autre raison d’utiliser des volumes de données avec parcimonie.

A [conteneur de volumes de données](https://docs.docker.com/v1.8/userguide/dockervolumes/) est une amélioration des volumes de données standard. Il est en fait un conteneur dormant qui possède un ou plusieurs volumes de données créées dans cette (comme décrit précédemment). Le conteneur de volume de données fournit l’accès aux conteneurs à partir d’un point de montage centrale. L’avantage de cette méthode d’accès est qu’il résume l’emplacement des données d’origine, qui effectue le conteneur de données à un point de montage logique. Il permet également à des conteneurs de « application » accèdent aux volumes de conteneur de données pour la création et la destruction tout en conservant les données persistantes dans un conteneur dédié.

Figure 4-5 indique que les volumes Docker standard peuvent être placés sur un stockage hors les conteneurs eux-mêmes, mais dans les limites physiques du serveur/machine virtuelle hôte. *Volumes docker n’ont pas la possibilité d’utiliser un volume à partir d’un ordinateur hôte serveur/machine virtuelle à un autre*.

![](./media/image5.png)

Figure 4-5 : volumes de données et sources de données externes pour les applications de conteneurs/conteneurs

En raison de l’incapacité à gérer les données partagées entre les conteneurs qui s’exécutent sur des hôtes physiques distincts, il est recommandé de pas utiliser des volumes de données d’entreprise, sauf si l’hôte Docker est un ordinateur hôte/virtuel fixe, car lorsque vous utilisez des conteneurs Docker dans un orchestrator, conteneurs doivent être déplacées vers un autre hôte, selon les optimisations à effectuer par le cluster.

Par conséquent, les volumes de données régulières sont un bon mécanisme pour travailler avec les fichiers de trace, fichiers temporelle ou de concept similaire qui n’affecte pas la cohérence des données métier si ou lorsque vos conteneurs sont déplacés sur plusieurs ordinateurs hôtes.

Comme les plug-ins de volume [Flocker](https://clusterhq.com/flocker/) fournissent des données sur tous les hôtes dans un cluster. Bien que pas tous les plug-ins de volume sont créés de manière égale, plug-ins de volume généralement fournir externalisés le stockage persistant fiable à partir des conteneurs immuables.

Sources de données distantes et les caches comme base de données SQL, DocumentDB ou un cache à distance comme Redis serait identique développement sans conteneurs. Il s’agit d’une des manières préférés et éprouvée, pour stocker les données d’application métier.


>[!div class="step-by-step"]
[Précédente] (monolithique applications.md) [suivant] (soa-applications.md)
