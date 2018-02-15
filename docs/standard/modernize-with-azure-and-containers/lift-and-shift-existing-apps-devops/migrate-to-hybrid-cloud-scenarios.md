---
title: "Migrer vers les scénarios de cloud hybride"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Migrer vers les scénarios de cloud hybride"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/2/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 61b22e48afd543ac077ebb4fe1b7be200f9ec859
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Migrer vers les scénarios de cloud hybride

Certaines organisations et les entreprises ne peut pas migrer certaines de leurs applications vers les clouds publics tels que Microsoft Azure, ou n’importe quel autre cloud public en raison des réglementations ou leurs propres stratégies. Toutefois, il est probable que toute organisation peut bénéficier de l’utilisation de certaines de leurs applications dans le cloud public et autres applications locales. Mais l’excès de complexité dans les environnements en raison des différentes plateformes et technologies utilisées dans des clouds publics et les environnements sur site risque d’un environnement mixte.

Microsoft fournit la meilleure solution de cloud hybride, une dans laquelle vous pouvez optimiser vos ressources existantes sur site et dans le cloud public, alors que vous vous assurez que dans un cloud hybride Azure. Vous pouvez optimiser les compétences et obtenir une approche unifiée flexible pour la création d’applications qui peuvent s’exécuter dans le cloud ou localement, grâce à Azure pile (local) et Azure (nuage public).

Lorsqu’il s’agit de sécurité, vous pouvez centraliser la gestion et sécurité sur votre cloud hybride. Vous pouvez contrôler tous les éléments multimédias, à partir de votre centre de données dans le cloud, en fournissant une authentification unique sur local et des applications de cloud. Pour cela en étendant Active Directory à un cloud hybride et à l’aide de la gestion d’identité.

Enfin, vous pouvez distribuer et analyser les données en toute transparence, utiliser les mêmes langages de requête pour les ressources de cloud et locales et appliquer analytique et la profondeur d’apprentissage dans Azure pour enrichir vos données, quelle que soit sa source.

## <a name="azure-stack"></a>Pile Azure

Pile Azure est une plateforme de cloud hybride qui vous permet de fournir des services Azure à partir du centre de données de votre organisation. Pile Azure est conçu pour prendre en charge de nouvelles options pour vos applications modernes dans des scénarios clés, telles que le bord et des environnements non connectées ou des exigences de conformité et de sécurité spécifiques de réunion.

Figure 4-13 montre une vue d’ensemble de la plateforme de cloud hybride true offertes par Microsoft.

![Plateforme de cloud hybride de Microsoft avec la pile d’Azure et Azure](./media/image13.jpg)

> **Figure 4-13.** Plateforme de cloud hybride de Microsoft avec la pile d’Azure et Azure

Pile Azure est proposé dans les deux options de déploiement pour répondre à vos besoins :

-   Pile Azure les systèmes intégrés

-   Kit de développement de pile Azure

### <a name="azure-stack-integrated-systems"></a>Pile Azure les systèmes intégrés

Systèmes de pile intégré Azure sont offerts par un partenariat de partenaires Microsoft et de matériel. Le partenariat crée une solution qui offre à rythme cloud innovation qui est équilibrée avec simplicité de gestion. Car Azure pile est proposé comme un système intégré de matériel et logiciel, vous obtenez la quantité exacte de flexibilité et de contrôle, lors de l’adoption toujours de l’innovation à partir du cloud. Les systèmes de pile intégré Azure de plage de taille de 4 à 12 nœuds et prise en charge conjointement par le partenaire de matériel et Microsoft. Systèmes de pile Azure intégré permet d’implémenter de nouveaux scénarios pour vos charges de travail de production.

### <a name="azure-stack-development-kit"></a>Kit de développement de pile Azure

Kit de développement Microsoft Azure pile est un déploiement à un seul nœud de pile Azure, ce qui vous permet d’évaluer et d’en savoir plus sur la pile de Azure. Vous pouvez également utiliser le Kit de développement de pile Azure comme environnement de développement, où vous pouvez développer à l’aide des API et des outils qui sont compatibles avec Azure. Kit de développement Azure pile n’est pas destinée à être utilisé comme un environnement de production.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Cloud hybride Azure**

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   **Azure Stack**

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   **Comptes de Service Active Directory pour les conteneurs Windows**

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   **Créer un conteneur avec prise en charge d’Active Directory**

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   **Le Gestionnaire de licences Azure hybride avantage**

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
[Précédent](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[Suivant](../walkthroughs-technical-get-started-overview.md)
