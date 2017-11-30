---
title: "État et les données dans les applications de Docker"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | État et les données dans les applications de Docker"
keywords: Docker, Microservices, ASP.NET, conteneur, SQL, CosmosDB, Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 36d0fb9f27ef56b36c380e2fc972c79cff77003e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="state-and-data-in-docker-applications"></a>État et les données dans les applications de Docker

Dans la plupart des cas, vous pouvez considérer un conteneur sous la forme d’une instance d’un processus. Un processus ne conserve pas l’état persistant. Même si un conteneur peut écrire dans un stockage local, en supposant qu’une instance sera autour indéfiniment serait en supposant qu’un seul emplacement dans la mémoire sera durable. Les images de conteneur, telles que des processus, doivent être évalués à plusieurs instances ou qu’ils seront finalement supprimées ; s’ils sont gérés par un orchestrateur de conteneur, il doit être supposé qu’ils peuvent obtenir déplacés à partir d’un nœud ou une machine virtuelle à un autre.

Docker fournit une fonctionnalité nommée la *superposition de système de fichiers*. Il implémente une tâche de copie sur écriture que magasins mis à jour les informations au système de fichiers racine du conteneur. Ces informations sont en outre à l’image d’origine sur laquelle repose le conteneur. Si le conteneur est supprimé du système, ces modifications sont perdues. Par conséquent, bien qu’il soit possible d’enregistrer l’état d’un conteneur dans son emplacement de stockage local, vous concevez un système de contourner ce problème serait en conflit avec le principe de conception de conteneur, qui est sans état par défaut.

Les solutions suivantes permettent de gérer les données persistantes dans les applications de Docker :

-   [Volumes de données](https://docs.docker.com/engine/tutorials/dockervolumes/) qui monter sur l’ordinateur hôte.

-   [Conteneurs de volumes de données](https://docs.docker.com/engine/tutorials/dockervolumes/#creating-and-mounting-a-data-volume-container) qui fournissent un stockage partagé entre les conteneurs à l’aide d’un conteneur externe.

-   [Plug-ins de volume](https://docs.docker.com/engine/tutorials/dockervolumes/) qui monter des volumes services à distance, en fournissant la persistance à long terme.

-   [Le stockage Azure](https://docs.microsoft.com/azure/storage/), qui fournit un stockage géo-distribuable, en fournissant une bonne solution de persistance à long terme pour les conteneurs.

-   Comme les bases de données relationnelles [base de données SQL Azure](https://azure.microsoft.com/services/sql-database/) ou bases de données NoSQL comme [base de données Azure Cosmos](https://docs.microsoft.com/azure/cosmos-db/introduction), ou de mettre en cache des services tels que [Redis](https://redis.io/).

Les éléments suivants fournissent plus de détails sur ces options.

**Volumes de données** sont mappées à partir de l’hôte du système d’exploitation vers des répertoires dans les conteneurs de répertoires. Lorsque le code dans le conteneur a accès au répertoire que l’accès est en fait un répertoire sur le système d’exploitation hôte. Ce répertoire n’est pas lié à la durée de vie du conteneur lui-même et le répertoire est accessible à partir de code qui s’exécute directement sur le système d’exploitation hôte ou par un autre conteneur qui mappe le même répertoire hôte vers lui-même. Par conséquent, les volumes de données sont conçus pour rendre persistantes des données indépendamment de la durée de vie du conteneur. Si vous supprimez un conteneur ou d’une image à partir de l’hôte Docker, les données rendues persistantes dans le volume de données n’est pas supprimé. Les données d’un volume est accessible à partir de l’hôte du système d’exploitation.

**Conteneurs de volumes de données** sont une évolution des volumes de données standard. Un conteneur de volume de données est un conteneur simple qui a un ou plusieurs volumes de données qu’il contient. Le conteneur de volume de données fournit l’accès aux conteneurs à partir d’un point de montage centrale. Cette méthode d’accès aux données est pratique, car il permet de supprimer l’emplacement des données d’origine. Reste, son comportement est semblable à celle d’un volume de données classiques, donc les données sont rendues persistantes dans ce conteneur dédié indépendamment du cycle de vie des conteneurs de l’application.

Comme indiqué dans la Figure 4-5, les volumes Docker standard peuvent être stockées en dehors de conteneurs eux-mêmes, mais dans les limites physiques de la machine virtuelle ou le serveur hôte. Toutefois, les conteneurs Docker ne peut pas accéder à un volume à partir d’un ordinateur hôte serveur ou machine virtuelle à un autre. En d’autres termes, avec ces volumes, il n’est pas possible de gérer les données partagées entre les conteneurs qui s’exécutent sur différents hôtes Docker

![](./media/image5.png)

**Figure 4-5**. Volumes de données et sources de données externes pour les applications conteneur

En outre, lorsque les conteneurs Docker sont gérés par un orchestrateur, conteneurs peuvent « déplacer » entre les hôtes, selon les optimisations effectuées par le cluster. Par conséquent, il n’est pas recommandé d’utiliser des volumes de données pour les données d’entreprise. Mais ils sont un bon mécanisme pour travailler avec des fichiers de trace, les fichiers temporelle, ou similaire qui n’affecteront pas la cohérence des données métier.

**Plug-ins de volume** comme [Flocker](https://clusterhq.com/flocker/) fournir l’accès aux données sur tous les hôtes dans un cluster. Pas de tous les plug-ins de volume sont créés de manière égale, plug-ins de volume généralement fournir externalisés le stockage persistant fiable à partir des conteneurs immuables.

**Sources de données distantes et cache** des outils tels que la base de données SQL Azure, base de données Azure Cosmos ou un cache à distance comme Redis peut être utilisé dans placées dans des conteneurs applications la même façon qu’ils sont utilisés lors du développement sans conteneurs. Il s’agit d’un moyen éprouvé pour stocker les données d’application métier.

**Stockage Azure.** Données d’entreprise doit généralement être placée à des ressources externes ou des bases de données, comme le stockage Azure. Le stockage Azure, dans concrète, fournit les services suivants dans le cloud :

-   Stockage d’objets BLOB stocke des données d’objet non structurées. Un objet blob peut être n’importe quel type de données texte ou binaire, tels que les fichiers de document ou un support (images, fichiers audio et vidéo). Stockage d’objets BLOB est également appelé stockage d’objets.

-   Stockage de fichiers offre un stockage partagé pour les applications héritées à l’aide du protocole SMB standard. Machines virtuelles et services de cloud computing peuvent partager des données de fichier entre les composants d’application via des partages montés. Applications locales peuvent accéder aux fichiers dans un partage via l’API REST du service de fichiers.

-   Le stockage table stocke les jeux de données structurées. Stockage de table est un magasin de données d’attribut de clé NoSQL, qui permet le développement rapide et un accès rapide à de grandes quantités de données.

**Bases de données relationnelles et les bases de données NoSQL.** Il existe de nombreuses options pour les bases de données externes à partir de bases de données relationnelles telles que les bases de données SQL Server, PostgreSQL, Oracle ou NoSQL comme base de données Azure Cosmos, MongoDB, etc.. Ces bases de données ne vont pas être expliqués dans le cadre de ce guide, car elles sont dans un objet totalement différent.


>[!div class="step-by-step"]
[Précédente] (mettez en conteneur-monolithique-applications.md) [suivant] (service-oriented-architecture.md)
