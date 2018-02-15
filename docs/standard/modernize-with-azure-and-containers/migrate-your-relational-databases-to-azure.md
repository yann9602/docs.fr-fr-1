---
title: "Migrer vos bases de données relationnelles vers azure"
description: "Moderniser des Applications .NET existantes avec Azure Cloud et les conteneurs Windows | migrer vos bases de données relationnelles vers azure"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 221d8c2b837fb738425e26f3af4da895e4987212
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="migrate-your-relational-databases-to-azure"></a>Migrer vos bases de données relationnelles vers azure

Vision : Azure propose la migration de base de données la plus complète.

Dans Azure, vous pouvez migrer vos serveurs de base de données directement vers les machines virtuelles IaaS de (finesse pure et MAJ), ou vous pouvez migrer vers Azure SQL Database, pour les autres avantages. Base de données SQL Azure offre instance managée et les options de (DBaaS) complète de base de données-as-a-service. La figure 3-1 indique la base de données relationnelle plusieurs chemins de migration disponibles dans Azure.

![Chemins de migration de base de données dans Azure](./media/image3-1.png)

> **Figure 3-1.** Chemins de migration de base de données dans Azure

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Quand migrer vers la base de données SQL Azure une Instance gérée

Dans la plupart des cas, de base de données SQL Azure une Instance gérée sera la meilleure solution pour prendre en compte lorsque vous migrez vos données vers Azure. Si vous migrez les bases de données SQL Server et que vous avez besoin de presque 100 % assurance que vous n’aurez pas à l’architecture de votre application ou d’apporter des modifications à vos données ou le code d’accès aux données, choisissez la fonctionnalité d’une Instance gérée de la base de données SQL Azure.

L’Instance gérée de la base de données Azure SQL est la meilleure option si vous avez des exigences supplémentaires pour les fonctionnalités au niveau de l’instance de SQL Server, ou que les conditions d’isolation au-delà des fonctionnalités fournies dans une base de données SQL Azure standard (modèle de base de données unique). Cette dernière n’est pas le choix plus orientée services PaaS, mais il n’offre pas les mêmes fonctionnalités que celui de SQL server traditionnel. La migration peut surface frictions.

Par exemple, une organisation de nos investissements dans les fonctionnalités de niveau de l’instance SQL Server bénéficient d’une migration vers l’Instance gérée de SQL. Exemples de fonctionnalités de SQL Server au niveau de l’instance incluent SQL intégration common language runtime (CLR), l’Agent SQL Server et interrogation des bases de données croiséesent. Prise en charge de ces fonctionnalités ne sont pas disponibles dans Azure SQL Database standard (un modèle de base de données unique).

Une organisation qui fonctionne dans un secteur de réglementation et qui a besoin garantir l’isolation pour des raisons de sécurité peut également bénéficier de choisir le modèle d’Instance gérée de SQL.

Instance gérée dans la base de données SQL Azure présente les caractéristiques suivantes :

-   Isolation de sécurité via le réseau virtuel Azure

-   Compatibilité d’aire de conception application, ces fonctionnalités :

    -   L’Agent SQL Server et SQL Server Profiler

    -   Réplication de références et les requêtes SQL CLR, des bases de données croisées, capture de données modifiées (CDC) et Service Broker

-   Jusqu'à 35 To des tailles de base de données

-   Migration de l’interruption de service minimum, avec ces fonctionnalités :

    -   Service de Migration de base de données Azure

    -   Sauvegarde en mode natif et de restauration et d’envoi de journaux

Grâce à ces fonctionnalités, lorsque vous migrez des bases de données application existantes à la base de données SQL Azure, le modèle d’une Instance gérée offre presque 100 % des avantages de Paas pour SQL Server. Instance managée est un environnement de SQL Server où vous continuez à l’aide des fonctionnalités de niveau de l’instance sans modifier la conception de votre application.

Instance managée est sans doute le mieux pour les entreprises qui en sont à l’aide de SQL Server, et pour lesquelles une grande souplesse dans la sécurité du réseau dans le cloud. Il ressemble à avoir un réseau virtuel privé pour vos bases de données SQL.

## <a name="when-to-migrate-to-azure-sql-database"></a>Quand migrer vers la base de données SQL Azure 

Comme indiqué, la base de données SQL Azure standard est un DBaaS entièrement géré et relationnelles. Base de données SQL gère actuellement des millions de bases de données de production, dans des centres de 38 données, dans le monde entier. Il prend en charge un large éventail d’applications et charges de travail, de la gestion des données transactionnelles simples, à gérant les applications critiques, de plus grandes consommatrices de données qui nécessitent un traitement de données avancé à une échelle globale.

En raison de ses fonctionnalités PaaS complètes et une meilleure tarification- et finalement coût-vous devez déplacer la base de données SQL Azure standard votre choix « par défaut » si vous avez une application qui utilise basique, standard SQL bases de données et aucune fonctionnalité d’instance supplémentaires. Fonctionnalités de SQL Server comme l’intégration CLR SQL, l’Agent SQL Server et l’interrogation des bases de données croisées ne sont pas pris en charge dans la base de données SQL Azure standard. Ces fonctionnalités sont disponibles uniquement dans le modèle de base de données SQL Azure une Instance gérée.

Base de données SQL Azure est le service de base de données de cloud uniquement intelligent qui est généré pour les développeurs d’applications. Il est également le seul service de base de données de cloud qui s’adapte à la volée, sans temps mort, pour vous aider à optimiser les applications mutualisées. Pour finir, base de données SQL Azure ne vous reste plus de temps à innover et elle accélère sur le marché. Vous pouvez créer des applications sécurisées et vous connecter à votre base de données SQL en utilisant les langages et les plateformes que vous préférez.

Base de données SQL Azure offre les avantages suivants :

-   Intelligence intégrée (apprentissage) qui apprend et s’adapte à votre application

-   Configuration de la base de données à la demande

-   Une plage d’offres, pour toutes les charges de travail

-   disponibilité de 99,99 % SLA, zéro maintenance

-   Géo-réplication et restauration des services pour la protection des données

-   Point de base de données SQL Azure dans la fonctionnalité Restauration du temps

-   Compatibilité avec SQL Server 2016, y compris hybride et migration

La base de données SQL Azure standard est proche PaaS à la base de données SQL Azure une Instance gérée. Vous devez tenter de l’utiliser, si possible, car vous obtiendrez plus d’avantages à partir d’un cloud géré. Toutefois, base de données SQL Azure présente des différences clés de normal et les instances de SQL Server locale. Selon les exigences de base de données de votre application existante et vos besoins de l’entreprise et les stratégies, il ne peut pas être le meilleur choix lorsque vous planifiez votre migration vers le cloud.

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>Transfert de votre SGBDR d’origine à une machine virtuelle (IaaS)

Une de vos options de migration consiste à déplacer votre d’origine système de gestion de base de données relationnelle (SGBDR), notamment Oracle, IBM DB2, MySQL, PostgreSQL ou SQL Server, à un serveur similaire qui s’exécute sur une machine virtuelle Azure. Si vous avez des applications existantes qui nécessitent la migration plus rapide pour le cloud avec des modifications minimes, ou aucune modification du tout, une migration directe vers IaaS dans le cloud peut être une option équitable. Il ne peut pas être la meilleure façon de tirer parti des avantages de l’ensemble du cloud, mais il est probablement le chemin d’accès initial plus rapide.

Actuellement, Microsoft Azure prend en charge jusqu'à [des serveurs de base de données différente 331](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) déployé en tant que machines virtuelles IaaS. Il s’agit notamment de RDBMSes populaires tels que SQL Server, Oracle, MySQL, PostgreSQL et IBM DB2 et plusieurs autres bases de données NoSQL, MongoDB, Cassandra, DataStax, MariaDB et Cloudera.

> [!NOTE]
> Bien que le déplacement de votre SGBDR pour une machine virtuelle Azure peut être le moyen le plus rapide pour migrer vos données vers le cloud (car il est IaaS), cette approche nécessite un investissement important dans vos équipes informatiques (administrateurs de base de données et aux professionnels de l’informatique). Les équipes d’entreprise doivent être en mesure de configurer et gérer la haute disponibilité, la récupération d’urgence et la mise à jour corrective pour SQL Server. Ce contexte doit également un environnement personnalisé, avec des droits d’administration complets.

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>Quand effectuer la migration vers SQL Server dans une machine virtuelle (IaaS)

Il peut y avoir quelques cas où vous devrez migrer vers SQL Server en tant qu’une machine virtuelle standard. Un exemple de scénario est si vous devez utiliser SQL Server Reporting Services. Dans la plupart des cas, cependant, base de données SQL Azure une Instance gérée peut fournir tout ce que vous devez migrer à partir de serveurs de SQL Server locale, la migration vers une machine virtuelle SQL Server ne doit donc être votre dernier recours pour essayer.

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Utiliser le Service de Migration de base de données Azure à migrer vos bases de données relationnelles vers Azure 

Vous pouvez utiliser le Service de Migration de base de données Azure pour migrer des bases de données relationnelles telles que SQL Server, Oracle et MySQL sur Azure, si votre base de données cible est la base de données SQL Azure, base de données SQL Azure une Instance gérée ou SQL Server sur une machine virtuelle Azure.

Le flux de travail automatisé, avec évaluation de la création de rapports, vous guide dans les modifications que vous devez faire avant de migrer la base de données. Lorsque vous êtes prêt, le service migre la base de données source vers Azure.

Chaque fois que vous modifiez un SGBDR d’origine, vous devrez peut-être tester à nouveau. Vous devrez peut-être modifier le code de mappage relationnel objet (ORM) dans votre application, en fonction des résultats des tests ou de phrases SQL.

Si vous avez une autre base de données (par exemple, IBM DB2) et opter pour une approche de courbes d’élévation et MAJ, vous souhaiterez continuer à utiliser ces bases de données en tant que machines virtuelles de IaaS dans Azure, sauf si vous êtes prêt à effectuer une migration de données plus complexe. Une migration de données plus complexe nécessitera effort supplémentaire, car vous devez migration à un type de base de données différents avec le nouveau schéma et les bibliothèques de programmation différents.

Pour savoir comment migrer des bases de données à l’aide du Service de Migration de base de données Azure, consultez [obtenir dans le cloud plus rapidement avec la base de données SQL Azure une Instance gérée et du Service de Migration de base de données Azure](https://channel9.msdn.com/Events/Build/2017/P4008).

## <a name="additional-resources"></a>Ressources supplémentaires

-   **Choisissez une option de SQL Server cloud : base de données SQL Azure (PaaS) ou SQL Server sur une machine virtuelle de Azure (IaaS)**

    [https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)

-   **Obtenir dans le cloud plus rapidement avec la base de données SQL Azure une Instance gérée et le Service de Migration de base de données**

    [https://channel9.msdn.com/Events/Build/2017/P4008](https://channel9.msdn.com/Events/Build/2017/P4008)

-   **Migration de base de données SQL Server pour la base de données SQL dans le cloud**

    [https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate](https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate)

-   **Azure SQL Database**

    [https://azure.microsoft.com/services/sql-database/?v=16.50](https://azure.microsoft.com/services/sql-database/?v=16.50)

-   **SQL Server sur des machines virtuelles**

    [https://azure.microsoft.com/services/virtual-machines/sql-server/](https://azure.microsoft.com/services/virtual-machines/sql-server/)

>[!div class="step-by-step"]
[Précédent](lift-and-shift-existing-apps-azure-iaas.md)
[Suivant](lift-and-shift-existing-apps-devops/index.md)