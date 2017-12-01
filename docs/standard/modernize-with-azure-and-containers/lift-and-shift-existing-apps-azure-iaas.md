---
title: "Déplacer des applications existantes IaaS Azure"
description: Moderniser des Applications .NET existantes avec Azure Cloud et les conteneurs Windows.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 7f7715bb0ec323874271a7e9ce1c666e23e33b22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="lift-and-shift-existing-apps-azure-iaas"></a>Déplacer des applications existantes IaaS Azure

> Vision : dans un premier temps, afin de réduire votre local investissement et coût total du matériel et de maintenance, de mise en réseau réhébergement simplement vos applications existantes dans le cloud.

Avant d’entrer dans *comment* pour migrer vos applications existantes à l’infrastructure Azure comme plateforme de service (IaaS), il est important d’analyser les raisons *pourquoi* vous ne souhaitez pas migrer directement vers IaaS dans Azure. Le scénario à ce niveau de maturité modernisation consiste essentiellement à démarrer à l’aide de machines virtuelles dans le cloud, au lieu de continuer à utiliser votre infrastructure locale actuelle.

Un autre point à analyser est *pourquoi* vous pouvez choisir de migrer vers pure nuage IaaS au lieu d’ajouter simplement la plus avancée des services gérés dans Azure. Vous devez déterminer quel cas peuvent nécessiter IaaS en premier lieu.

Figure 2-1 positionne les applications Cloud Infrastructure prêt dans les niveaux de maturité modernisation :

![Positionnement des applications de l’Infrastructure prête pour le Cloud](./media/image2-1.png)

> **Figure 2-1.** Positionnement des applications de l’Infrastructure prête pour le Cloud

## <a name="why-migrate-existing-net-web-applications-to-azure-iaas"></a>Pourquoi effectuer la migration des applications web .NET existantes vers Azure IaaS 

La principale raison pour migrer vers le cloud, même au niveau IaaS initial, est de réduire les coûts. À l’aide des services d’infrastructure gérés plus, votre organisation peut réduire son placement dans la maintenance du matériel serveur ou approvisionnement d’ordinateurs virtuels et de déploiement et gestion de l’infrastructure.

Après avoir apporté la décision de migrer vos applications vers le cloud, la raison principale raison pour laquelle vous pouvez choisir IaaS au lieu des options plus avancées telles que PaaS est simplement que l’environnement IaaS sera plus facile. Déplacement vers un environnement qui est similaire à votre, environnement local offre une courbe d’apprentissage plus faible, ce qui rend le chemin d’accès le plus rapide pour le cloud.

Toutefois, le chemin d’accès rapide être redirigé vers le cloud ne signifie pas que vous bénéficierez le meilleur parti de l’utilisation de vos applications en cours d’exécution dans le cloud. Toute organisation bénéficierez plus des avantages d’une migration de cloud au niveau déjà introduites DevOps prête pour le Cloud et PaaS (optimisée pour le Cloud) une échéance.

Il est également devenu évident que les applications sont plus faciles à moderniser et redéfinir l’architecture à l’avenir lorsqu’ils sont déjà en cours d’exécution dans le cloud, même sur IaaS. Cela est vrai en partie parce que la migration de données d’application a déjà été atteint. En outre, votre organisation sera ont acquis les compétences nécessaires pour travailler dans le cloud et la touche MAJ enfoncée pour fonctionne en une « culture cloud ».

## <a name="when-to-migrate-to-iaas-instead-of-to-paas"></a>Quand migrer vers IaaS au lieu de vers PaaS

Les sections suivantes, abordés dans les applications DevOps prête pour le Cloud qui sont principalement basées sur les services et plateformes de PaaS. Ces applications vous donnent la plupart des avantages à partir de la migration vers le cloud.

Si votre objectif consiste simplement à déplacer des applications existantes vers le nuage, tout d’abord, identifiez les applications existantes qui nécessitent une modification importante pour s’exécuter dans Azure App Service. Ces applications doivent être les premières à être.

Ensuite, si vous ne souhaitez pas, ou encore ne peut pas atteindre les conteneurs Windows et ou orchestrators comme Azure Service Fabric ou Kubernetes, encore, puis est lorsque vous utilisez bruts machines virtuelles (IaaS).

Toutefois, gardez à l’esprit que correctement configuration, la sécurisation et la gestion des ordinateurs virtuels nécessitent beaucoup plus de temps et de ressources informatiques par rapport à l’aide des services PaaS dans Azure. Si vous envisagez de Machines virtuelles Azure, veillez à prendre en compte l’effort de maintenance continue pour les corriger, de mettre à jour et de gérer votre environnement de machine virtuelle. Machines virtuelles est IaaS.

## <a name="use-azure-migrate-to-analyze-and-migrate-your-existing-applications-to-azure"></a>Utilisez Azure migrer pour analyser et de migrer vos applications existantes vers Azure

Migration vers le nuage ne doit pas nécessairement être difficile. Mais de nombreuses organisations s’efforcent de prise en main - pour obtenir une visibilité approfondie dans l’environnement et les interdépendances étroits entre les applications, les charges de travail et les données. Sans cette visibilité, il peut être difficile de planifier le chemin d’accès vers l’avant. Sans les informations détaillées sur les étapes nécessaires pour réussir la migration, vous ne pouvez avoir les conversations droit au sein de votre organisation. Vous ne connaissez pas suffisamment les éventuelles économiques, ou si les charges de travail peut simplement finesse-et-MAJ nécessiteraient des modifications importantes à la migration. Pas étonnant que de nombreuses organisations hésitent.

[Migration d’Azure](https://aka.ms/azuremigrate) est un service qui fournit des conseils, des analyses et les mécanismes nécessaires pour vous aider à migrer vers Azure. Migration d’Azure fournit :

-   Découverte et évaluation pour les ordinateurs virtuels de local

-   Mappage des dépendances intégrés pour la découverte de haut degré de confiance des applications à plusieurs niveaux

-   Restructuration intelligente pour les machines virtuelles

-   Création de rapports avec des recommandations pour la correction des problèmes potentiels de compatibilité

-   Intégration avec le Service de gestion de base de données Azure pour la découverte de base de données et de migration

Migration d’Azure vous êtes ainsi sûr que vos charges de travail peuvent migrer avec un impact minimal sur l’entreprise et s’exécuter comme prévu dans Azure. Avec les outils et les instructions, vous pouvez obtenir maximal retour sur investissement tout en garantissant que les performances critiques et fiabilité aux besoins.

Figure 2-2 indique le mappage de dépendance intégrées pour toutes les connexions de serveur et d’application effectué par la migration d’Azure.

![Positionnement des applications de l’Infrastructure prête pour le Cloud](./media/image2-2.png)

> **Figure 2-2.** Positionnement des applications de l’Infrastructure prête pour le Cloud

## <a name="use-azure-site-recovery-to-migrate-your-existing-vms-to-azure-vms"></a>Azure Site Recovery permet de migrer vos ordinateurs virtuels existants pour les machines virtuelles Azure

Dans le cadre de bout en bout [Azure migrer](https://aka.ms/azuremigrate), [Azure Site Recovery](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview) est un outil qui vous permet de facilement migrer vos applications web vers les machines virtuelles dans Azure. Vous pouvez utiliser le Site Recovery pour répliquer des machines virtuelles de locaux et des serveurs physiques vers Azure, ou pour les répliquer vers un emplacement de site secondaire. Vous pouvez répliquer même une charge de travail qui s’exécute sur une machine virtuelle Azure pris en charge, sur un site local *Hyper-V* machine virtuelle, dans un *VMware* machine virtuelle, ou sur un serveur physique Windows ou Linux. La réplication vers Azure élimine le coût et la complexité de la gestion d’un centre de données secondaire.

Récupération de site est également mise en particulier pour les environnements hybrides qui sont en partie local et en partie sur Azure. Récupération de site permet de garantir la continuité d’activité en conservant vos applications qui s’exécutent sur des machines virtuelles locaux et sur les serveurs physiques disponibles si un site tombe en panne. Elle réplique les charges de travail qui sont exécutent sur des machines virtuelles et des serveurs physiques afin qu’ils restent disponibles dans un emplacement secondaire si le site principal n’est pas disponible. Il récupère les charges de travail et du site principal lorsque c’est à nouveau d’exécuter.

Figure 2-3 illustre l’exécution de plusieurs migrations d’ordinateur virtuel à l’aide d’Azure Site Recovery.

![Positionnement des applications de l’Infrastructure prête pour le Cloud](./media/image2-3.png)

> **Figure 2-3.** Positionnement des applications de l’Infrastructure prête pour le Cloud

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Azure migrer la feuille de données**

    [https://aka.ms/azuremigration\_feuille de données](https://aka.ms/azuremigration\_datasheet)

-   **Migrer de Azure**

    [http://azuremigrationcenter.com/](http://azuremigrationcenter.com/)

-   **Migrer vers Azure Site Recovery**

    [https://docs.Microsoft.com/Azure/Site-Recovery/Site-Recovery-Migrate-to-Azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-to-azure)

-   **Vue d’ensemble des services Azure Site Recovery**

    [https://docs.Microsoft.com/Azure/Site-Recovery/Site-Recovery-Overview](https://docs.microsoft.com/azure/site-recovery/site-recovery-overview)

-   **Migration de machines virtuelles dans AWS aux machines virtuelles Azure**

    [https://docs.Microsoft.com/Azure/Site-Recovery/Site-Recovery-Migrate-AWS-to-Azure](https://docs.microsoft.com/azure/site-recovery/site-recovery-migrate-aws-to-azure)

>[!div class="step-by-step"]
[Précédent](index.md)
[Suivant](migrate-your-relational-databases-to-azure.md)
