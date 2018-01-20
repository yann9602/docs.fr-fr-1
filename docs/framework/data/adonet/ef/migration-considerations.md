---
title: "Considérations sur la migration (Entity Framework)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8e4c1b06e5a3a7717b99379fd9bca2c5a8a14a6a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="migration-considerations-entity-framework"></a>Considérations sur la migration (Entity Framework)
[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Entity Framework présente plusieurs avantages pour une application existante. La possibilité d'utiliser un modèle conceptuel pour séparer des structures de données utilisées par l'application du schéma de la source de données constitue l'un de ces avantages les plus importants. Cela vous permet d'apporter facilement des modifications à venir au modèle de stockage ou à la source de données eux-mêmes sans apporter de modifications de compensation à l'application. Pour plus d’informations sur les avantages de l’utilisation de la [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], consultez [présentation d’Entity Framework](../../../../../docs/framework/data/adonet/ef/overview.md) et [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 Pour tirer parti des avantages de la [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], vous pouvez migrer une application existante vers le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Certaines tâches sont communes à toutes les applications migrées. Ces tâches communes incluent la mise à niveau de l’application pour utiliser le [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] depuis la version 3.5 Service Pack 1 (SP1), définition des modèles et mappage et configuration d’Entity Framework. Lorsque vous effectuez la migration d'une application vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], des points supplémentaires sont à prendre en considération. Ces points dépendent du type d'application qui est migrée et des fonctionnalités spécifiques de l'application. Cette rubrique fournit des informations vous permettant de choisir la meilleure approche à utiliser lorsque vous mettez à niveau une application existante.  
  
## <a name="general-migration-considerations"></a>Considérations générales sur la migration  
 Les considérations suivantes s'appliquent lorsque vous effectuez la migration d'une application vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] :  
  
-   Toute application qui utilise le [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] depuis la version 3.5 SP1 peuvent être migrés vers Entity Framework, tant que le fournisseur de données pour la source de données qui est utilisé par l’application prend en charge Entity Framework.  
  
-   Il est possible qu’Entity Framework ne prenne pas en charge toutes les fonctionnalités d’un fournisseur de source de données, même si ce fournisseur prend en charge Entity Framework.  
  
-   Pour une application volumineuse ou complexe, vous n'êtes pas obligé de migrer la totalité de l'application vers Entity Framework à la fois. Toutefois, toute partie de l'application qui n'utilise pas Entity Framework doit néanmoins être modifiée lorsque la source de données change.  
  
-   La connexion de fournisseur de données utilisée par Entity Framework peut être partagée avec d'autres parties de votre application car [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilise des fournisseurs de données [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] pour accéder à la source de données. Par exemple, le fournisseur SqlClient est utilisé par Entity Framework pour accéder à une base de données SQL Server. Pour plus d’informations, consultez [fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## <a name="common-migration-tasks"></a>Tâches de migration communes  
 Le chemin d'accès pour effectuer la migration d'une application existante vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dépend à la fois du type d'application et de la stratégie d'accès aux données existante. Toutefois, vous devez toujours effectuer les tâches suivantes lorsque vous migrez une application existante vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
> [!NOTE]
>  Toutes ces tâches sont effectuées automatiquement lorsque vous utilisez les outils Entity Data Model avec [!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)] ou version ultérieure. Pour plus d’informations, consultez [Comment : utiliser l’Assistant Entity Data Model](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
1.  Mettez à niveau l'application.  
  
     Un projet créé à l’aide d’une version antérieure de [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] et [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] doit être mis à niveau pour utiliser [!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)] SP1 et [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] depuis la version 3.5 SP1.  
  
2.  Définissez les modèles et le mappage.  
  
     Les fichiers de modèle et de mappage définissent des entités dans le modèle conceptuel, des structures dans la source de données (telles que des tables, des procédures stockées et des vues), ainsi que le mappage entre les entités et les structures de la source de données. Pour plus d’informations, consultez [Comment : définir manuellement les fichiers de modèle et de mappage](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a).  
  
     Les types définis dans le modèle de stockage doivent correspondre aux noms des objets présents dans la source de données. Si l'application existante expose des données en tant qu'objets, vous devez vous assurer que les entités et les propriétés définies dans le modèle conceptuel correspondent aux noms de ces classes de données et propriétés existantes. Pour plus d’informations, consultez [Comment : personnaliser la modélisation et mappage des fichiers pour travailler avec des objets personnalisés](http://msdn.microsoft.com/library/bb40c4db-0121-4e45-a167-8fb06707a708).  
  
    > [!NOTE]
    >  Entity Data Model Designer peut être utilisé pour renommer des entités du modèle conceptuel afin qu'elles correspondent à des objets existants. Pour plus d’informations, consultez [Entity Data Model Designer](http://msdn.microsoft.com/library/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf).  
  
3.  Définissez la chaîne de connexion.  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilise une chaîne de connexion spécialement mise en forme lors de l'exécution de requêtes sur un modèle conceptuel. Cette chaîne de connexion encapsule des informations relatives aux fichiers de modèle et de mappage et à la connexion à la source de données. Pour plus d’informations, consultez [Comment : définir la chaîne de connexion](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md).  
  
4.  Configurez le projet [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)].  
  
     Les références à des assemblys [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] et aux fichiers de modèle et de mappage doivent être ajoutées au projet [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)]. Vous pouvez ajouter ces fichiers de mappage au projet pour garantir qu'ils sont déployés avec l'application dans l'emplacement indiqué dans la chaîne de connexion. Pour plus d’informations, consultez [Comment : configurer manuellement un projet Entity Framework](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
## <a name="considerations-for-applications-with-existing-objects"></a>Considérations relatives aux applications comportant des objets existants  
 À partir du [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] prend en charge des objets CLR (POCO) « simples », également appelés « objets ignorant la persistance ». Dans la plupart des cas, vos objets existants peuvent fonctionner avec [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] en effectuant des changements mineurs. Pour plus d’informations, consultez [utilisation des entités POCO](http://msdn.microsoft.com/library/5e0fb82a-b6d1-41a1-b37b-c12db61629d3). Vous pouvez également migrer une application à la [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] et utiliser les classes de données qui sont générés par les outils Entity Framework. Pour plus d’informations, consultez [Comment : utiliser l’Assistant Entity Data Model](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
## <a name="considerations-for-applications-that-use-adonet-providers"></a>Considérations relatives aux applications qui utilisent des fournisseurs ADO.NET  
 [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)]fournisseurs, tels que SqlClient, vous permettent d’interroger une source de données pour retourner des données tabulaires. Données peuvent également être chargées dans un [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] jeu de données. La liste suivante décrit des considérations relatives à la mise à niveau d'une application qui utilise un fournisseur [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] existant :  
  
 Affichage de données tabulaires à l'aide d'un lecteur de données.  
 Vous pouvez envisager d’exécuter un [!INCLUDE[esql](../../../../../includes/esql-md.md)] de requête à l’aide du fournisseur EntityClient et de l’énumération retourné <xref:System.Data.EntityClient.EntityDataReader> objet. Procédez de cette manière si votre application affiche des données tabulaires à l'aide d'un lecteur de données et ne requiert pas les fonctionnalités fournies par [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pour la matérialisation des données dans des objets, le suivi des modifications et l'exécution des mises à jour. Vous pouvez continuer à utiliser le code d'accès aux données existant qui effectuer des mises à jour dans la source de données, mais vous pouvez utiliser la connexion existante accessible à partir de la propriété <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> de l'objet <xref:System.Data.EntityClient.EntityConnection>. Pour plus d’informations, consultez [fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 Utilisation de datasets.  
 Le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] fournit de nombreuses fonctionnalités fournies par le DataSet, y compris la persistance en mémoire, suivi des modifications, la liaison de données et sérialisation des objets en tant que données XML. Pour plus d’informations, consultez [utilisation des objets](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Si le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ne fournit pas les fonctionnalités du DataSet requises par votre application, vous pouvez toujours bénéficier des avantages des requêtes LINQ à l’aide de [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)]. Pour plus d’informations, [consultez LINQ to DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="considerations-for-applications-that-bind-data-to-controls"></a>Considérations relatives aux applications qui lient des données à des contrôles  
 Le [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] vous permet d’encapsuler des données dans une source de données, comme un DataSet ou un [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] contrôle de source de données et puis lier les éléments d’interface utilisateur à ces contrôles de données. La liste suivante décrit les considérations concernant la liaison de contrôles à des données Entity Framework.  
  
 Liaison de données à des contrôles.  
 Lorsque vous interrogez le modèle conceptuel, le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] retourne les données sous forme d’objets qui sont des instances de types d’entités. Ces objets peuvent être liés directement à des contrôles, et cette liaison prend en charge les mises à jour. Cela signifie que les modifications apportées aux données dans un contrôle, par exemple une ligne dans un <xref:System.Windows.Forms.DataGridView>, automatiquement enregistrées dans la base de données lors de la <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> méthode est appelée.  
  
 Si votre application énumère les résultats d'une requête pour afficher des données dans un objet <xref:System.Windows.Forms.DataGridView> ou un autre type de contrôle que prend en charge la liaison de données, vous pouvez modifier votre application pour lier le contrôle au résultat d'un objet <xref:System.Data.Objects.ObjectQuery%601>.  
  
 Pour plus d’informations, consultez [liaison d’objets aux contrôles](http://msdn.microsoft.com/library/2fd34855-929b-4303-a91e-4bb69d958f2b).  
  
 Contrôles de source de données [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  
 Le [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclut un contrôle de source de données conçu pour simplifier la liaison de données dans [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] des applications Web. Pour plus d’informations, consultez [contrôle de Source de données Entity Framework](http://msdn.microsoft.com/library/1f09af00-9578-4744-a029-765710a3c83f).  
  
## <a name="other-considerations"></a>Autres considérations  
 Les remarques suivantes peuvent s'appliquer lorsque vous effectuez une migration de types spécifiques d'applications vers Entity Framework.  
  
 Applications qui exposent des services de données.  
 Les services Web et les applications basées sur Windows Communication Foundation (WCF) exposent les données d'une source de données sous-jacente en utilisant un format de messagerie de demande/réponse XML. [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] prend en charge la sérialisation d'objets entité en utilisant la sérialisation de contrat de données binaire, XML ou WCF. La sérialisation binaire et la sérialisation WCF prennent tous les deux en charge la sérialisation complète de graphiques d'objets. Pour plus d’informations, consultez [génération d’Applications multicouches](http://msdn.microsoft.com/library/9439d2ba-6b5f-44e8-be65-8a442d922cbb).  
  
 Applications qui utilisent des données XML.  
 La sérialisation des objets vous permet de créer des services des données [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Ces services fournissent des données à des applications qui utilisent des données XML, telles que les applications Internet AJAX. Dans ces cas, envisagez d'utiliser [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)]. Ces services de données sont basées sur l’Entity Data Model fournissent un accès dynamique aux données d’entité à l’aide des actions de transfert REST (Representational State) HTTP standard, tels que GET, PUT et post-déploiement. Pour plus d’informations, consultez [Services de données WCF 4.5](../../../../../docs/framework/data/wcf/index.md).  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ne prend pas en charge le type de données XML natif. Cela signifie que, lorsqu'une entité est mappée à une table avec une colonne XML, la propriété d'entité équivalente de la colonne XML est une chaîne. Les objets peuvent être déconnectés et sérialisés sous forme de données XML. Pour plus d’informations, consultez [sérialisation d’objets](http://msdn.microsoft.com/library/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99).  
  
 Si votre application nécessite la possibilité d'interroger des données XML, vous pouvez tout de même tirer parti des avantages des requêtes LINQ en utilisant LINQ to XML. Pour plus d’informations, consultez [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).  
  
 Applications qui gèrent l'état.  
 [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)]Les applications Web doivent fréquemment gérer l’état d’une page Web ou d’une session utilisateur. Les objets dans une <xref:System.Data.Objects.ObjectContext> instance peut être stockée dans l’état d’affichage client ou dans l’état de session sur le serveur et ultérieurement récupérée et rattachée à un nouveau contexte de l’objet. Pour plus d’informations, consultez [attachement et détachement des objets](http://msdn.microsoft.com/library/41d5c1ef-1b78-4502-aa10-7e1438d62d23).  
  
## <a name="see-also"></a>Voir aussi  
 [Points à prendre en considération pour le déploiement](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)  
 [Terminologie Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md)
