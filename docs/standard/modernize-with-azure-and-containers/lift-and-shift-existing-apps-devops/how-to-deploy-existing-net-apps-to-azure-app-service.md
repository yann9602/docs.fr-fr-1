---
title: "Comment déployer des applications .NET existantes vers Azure App Service"
description: "Architecture de Microservices .NET pour les Applications .NET en conteneur | Comment déployer des applications .NET existantes vers Azure App Service"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 84bffe7aad6bbffb40519c9146d8156159d55850
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-deploy-existing-net-apps-to-azure-app-service"></a>Comment déployer des applications .NET existantes vers Azure App Service 

La fonctionnalité d’applications Web du Service d’application Azure est une plateforme de calcul entièrement géré qui est optimisée pour l’hébergement d’applications web et sites Web. Cette offre PaaS dans Microsoft Azure vous permet de vous concentrer sur votre logique métier, tandis que Azure prend en charge l’infrastructure pour exécuter et de faire évoluer vos applications.

## <a name="validate-sites-and-migrate-to-app-service-with-azure-app-service-migration-assistant"></a>Valider des sites et de migrer vers le Service d’application avec l’Assistant de Migration Azure App Service

Lorsque vous créez une nouvelle application dans Visual Studio, généralement déplacement de l’application au Service d’application est simple. Toutefois, si vous envisagez de migrer une application existante vers le Service d’applications, vous devez d’abord déterminer si toutes vos dépendances d’application sont compatibles avec le Service d’applications. Cela inclut les dépendances, telles que le serveur du système d’exploitation et tout logiciel tiers est installé sur le serveur.

Vous pouvez utiliser [Assistant de Migration Azure App Service](https://www.migratetoazure.net/) pour analyser des sites et les migrer à partir de serveurs web Windows et Linux pour le Service d’applications. Dans le cadre de la migration, l’outil crée des applications web et bases de données sur Azure en fonction des besoins, publie du contenu et publie votre base de données.

Azure App Service Assistant de Migration prend en charge la migration à partir d’IIS qui s’exécute sur Windows Server pour le cloud. Service d’applications prend en charge Windows Server 2003 et versions ultérieures.

> ![https://www.migratetoazure.net/Images/ImageCanvas.png](./media/image5.png)
>
> **Figure 4-5.** À l’aide de l’Assistant de Migration du Service d’applications Azure

Assistant de Migration App Service est un outil qui se déplace de vos sites Web à partir de vos serveurs web vers le cloud Azure.

Une fois un site Web est migré vers le Service d’applications, le site a tout ce dont il a besoin pour exécuter efficacement et en toute sécurité. Les sites sont définies et s’exécuter automatiquement dans le service de PaaS Azure cloud (Service d’application).

L’outil de migration du Service d’applications peut analyser vos sites Web et créer des rapports sur leur compatibilité pour le déplacement vers le Service d’applications. Si vous êtes satisfait de l’analyse, vous pouvez laisser l’Assistant Migration de Service application migrer le contenu, les données et les paramètres pour vous. Si un site n’est pas assez compatible, l’outil de migration vous indique ce que vous deviez ajuster pour qu’il fonctionne.

### <a name="additional-resources"></a>Ressources supplémentaires

-   **Assistant de Migration du Service d’applications Azure**

    [https://www.migratetoazure.net/](https://www.migratetoazure.net/)

>[!div class="step-by-step"]
[Précédent](what-about-cloud-optimized-applications.md)
[Suivant](deploy-existing-net-apps-as-windows-containers.md)
