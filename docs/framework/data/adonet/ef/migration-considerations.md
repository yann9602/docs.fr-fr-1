---
title: "Consid&#233;rations sur la migration (Entity Framework) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: c85b6fe8-cc32-4642-8f0a-dc0e5a695936
caps.latest.revision: 6
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Consid&#233;rations sur la migration (Entity Framework)
[!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] Entity Framework présente plusieurs avantages pour une application existante.  La possibilité d'utiliser un modèle conceptuel pour séparer des structures de données utilisées par l'application du schéma de la source de données constitue l'un de ces avantages les plus importants.  Cela vous permet d'apporter facilement des modifications à venir au modèle de stockage ou à la source de données eux\-mêmes sans apporter de modifications de compensation à l'application.  Pour plus d'informations sur les avantages liés à l'utilisation d'[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], consultez [Vue d'ensemble d'Entity Framework](../../../../../docs/framework/data/adonet/ef/overview.md) et [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
 Pour tirer parti des avantages d'[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], vous pouvez effectuer la migration d'une application existante vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Certaines tâches sont communes à toutes les applications migrées.  Ces tâches communes incluent la mise à niveau de l'application pour utiliser le [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] à partir de la version 3.5 Service Pack 1 \(SP1\), la définition des modèles et du mappage, et la configuration d'Entity Framework.  Lorsque vous effectuez la migration d'une application vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], des points supplémentaires sont à prendre en considération.  Ces points dépendent du type d'application qui est migrée et des fonctionnalités spécifiques de l'application.  Cette rubrique fournit des informations vous permettant de choisir la meilleure approche à utiliser lorsque vous mettez à niveau une application existante.  
  
## Considérations générales sur la migration  
 Les considérations suivantes s'appliquent lorsque vous effectuez la migration d'une application vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] :  
  
-   Toute application qui utilise [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] à partir de la version 3.5 SP1 peut être migrée vers Entity Framework, à condition que le fournisseur de données pour la source de données utilisée par l'application prenne en charge Entity Framework.  
  
-   Il est possible qu'Entity Framework ne prenne pas en charge toutes les fonctionnalités d'un fournisseur de source de données, même si ce fournisseur prend en charge Entity Framework.  
  
-   Pour une application volumineuse ou complexe, vous n'êtes pas obligé de migrer la totalité de l'application vers Entity Framework à la fois.  Toutefois, toute partie de l'application qui n'utilise pas Entity Framework doit néanmoins être modifiée lorsque la source de données change.  
  
-   La connexion de fournisseur de données utilisée par Entity Framework peut être partagée avec d'autres parties de votre application car [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilise des fournisseurs de données [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] pour accéder à la source de données.  Par exemple, le fournisseur SqlClient est utilisé par Entity Framework pour accéder à une base de données SQL Server.  Pour plus d'informations, consultez [Fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
## Tâches de migration communes  
 Le chemin d'accès pour effectuer la migration d'une application existante vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dépend à la fois du type d'application et de la stratégie d'accès aux données existante.  Toutefois, vous devez toujours effectuer les tâches suivantes lorsque vous migrez une application existante vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  
  
> [!NOTE]
>  Toutes ces tâches sont effectuées automatiquement lorsque vous utilisez les outils Entity Data Model avec [!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)] ou version ultérieure.  Pour plus d'informations, consultez [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/fr-fr/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
1.  Mettez à niveau l'application.  
  
     Un projet créé à l'aide d'une version antérieure de [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] et du [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] doit être mis à niveau pour utiliser [!INCLUDE[vsOrcas](../../../../../includes/vsorcas-md.md)] SP1 et [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 3.5 SP1 ou version ultérieure.  
  
2.  Définissez les modèles et le mappage.  
  
     Les fichiers de modèle et de mappage définissent des entités dans le modèle conceptuel, des structures dans la source de données \(telles que des tables, des procédures stockées et des vues\), ainsi que le mappage entre les entités et les structures de la source de données.  Pour plus d'informations, consultez [How to: Manually Define the Model and Mapping Files](http://msdn.microsoft.com/fr-fr/d4fd6864-f2a1-48f0-aa32-1e318775a99a).  
  
     Les types définis dans le modèle de stockage doivent correspondre aux noms des objets présents dans la source de données.  Si l'application existante expose des données en tant qu'objets, vous devez vous assurer que les entités et les propriétés définies dans le modèle conceptuel correspondent aux noms de ces classes de données et propriétés existantes.  Pour plus d'informations, consultez [How to: Customize Modeling and Mapping Files to Work with Custom Objects](http://msdn.microsoft.com/fr-fr/bb40c4db-0121-4e45-a167-8fb06707a708).  
  
    > [!NOTE]
    >  Entity Data Model Designer peut être utilisé pour renommer des entités du modèle conceptuel afin qu'elles correspondent à des objets existants.  Pour plus d'informations, consultez [Entity Data Model Designer](http://msdn.microsoft.com/fr-fr/4ccd7ad6-b934-4f7c-82a0-cfd2d4a95faf).  
  
3.  Définissez la chaîne de connexion.  
  
     [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] utilise une chaîne de connexion spécialement mise en forme lors de l'exécution de requêtes sur un modèle conceptuel.  Cette chaîne de connexion encapsule des informations relatives aux fichiers de modèle et de mappage et à la connexion à la source de données.  Pour plus d'informations, consultez [Procédure : définir la chaîne de connexion](../../../../../docs/framework/data/adonet/ef/how-to-define-the-connection-string.md).  
  
4.  Configurez le projet [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)].  
  
     Les références à des assemblys [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] et aux fichiers de modèle et de mappage doivent être ajoutées au projet [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)].  Vous pouvez ajouter ces fichiers de mappage au projet pour garantir qu'ils sont déployés avec l'application dans l'emplacement indiqué dans la chaîne de connexion.  Pour plus d'informations, consultez [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/fr-fr/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
## Considérations relatives aux applications comportant des objets existants  
 À partir du [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] prend en charge des objets CLR \(POCO\) « simples », également appelés « objets ignorant la persistance ».  Dans la plupart des cas, vos objets existants peuvent fonctionner avec [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] en effectuant des changements mineurs.  Pour plus d'informations, consultez [Working with POCO Entities](http://msdn.microsoft.com/fr-fr/5e0fb82a-b6d1-41a1-b37b-c12db61629d3). Vous pouvez également migrer une application vers [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] et utiliser les classes de données générées par les outils Entity Framework.  Pour plus d'informations, consultez [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/fr-fr/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
## Considérations relatives aux applications qui utilisent des fournisseurs ADO.NET  
 Les fournisseurs [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)], tels que SqlClient, vous permettent d'interroger une source de données pour retourner des données tabulaires.  Les données peuvent également être chargées dans un dataset [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)].  La liste suivante décrit des considérations relatives à la mise à niveau d'une application qui utilise un fournisseur [!INCLUDE[vstecado](../../../../../includes/vstecado-md.md)] existant :  
  
 Affichage de données tabulaires à l'aide d'un lecteur de données.  
 Vous pouvez envisager d'exécuter une requête [!INCLUDE[esql](../../../../../includes/esql-md.md)] à l'aide du fournisseur EntityClient et de passer en revue l'objet <xref:System.Data.EntityClient.EntityDataReader> retourné.  Procédez de cette manière si votre application affiche des données tabulaires à l'aide d'un lecteur de données et ne requiert pas les fonctionnalités fournies par [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] pour la matérialisation des données dans des objets, le suivi des modifications et l'exécution des mises à jour. Vous pouvez continuer à utiliser le code d'accès aux données existant qui effectuer des mises à jour dans la source de données, mais vous pouvez utiliser la connexion existante accessible à partir de la propriété <xref:System.Data.EntityClient.EntityConnection.StoreConnection%2A> de l'objet <xref:System.Data.EntityClient.EntityConnection>.  Pour plus d'informations, consultez [Fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).  
  
 Utilisation de datasets.  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclut de nombreuses fonctionnalités fournies par le DataSet, y compris la persistance en mémoire, le suivi des modifications, la liaison de données et la sérialisation des objets en tant que données XML.  Pour plus d'informations, consultez [Utilisation d'objets](../../../../../docs/framework/data/adonet/ef/working-with-objects.md).  
  
 Si [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ne fournissent pas les fonctionnalités du DataSet requises par votre application, vous pouvez quand même tirer parti des avantages des requêtes LINQ en utilisant [!INCLUDE[linq_dataset](../../../../../includes/linq-dataset-md.md)].  Pour plus d'informations, consultez [LINQ to DataSet](../../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## Considérations relatives aux applications qui lient des données à des contrôles  
 Le [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] vous permet d'encapsuler des données dans une source de données, telle qu'un DataSet ou un contrôle de source de données [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)], puis lie des éléments d'interface utilisateur à ces contrôles de données.  La liste suivante décrit les considérations concernant la liaison de contrôles à des données Entity Framework.  
  
 Liaison de données à des contrôles.  
 Lorsque vous interrogez le modèle conceptuel, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] retourne les données sous forme d'objets qui sont des instances de types d'entités.  Ces objets peuvent être liés directement à des contrôles, et cette liaison prend en charge les mises à jour. Cela signifie que les modifications apportées aux données dans un contrôle, telles qu'une ligne dans un objet <xref:System.Windows.Forms.DataGridView>, sont automatiquement enregistrées dans la base de données lorsque la méthode <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> est appelée.  
  
 Si votre application énumère les résultats d'une requête pour afficher des données dans un objet <xref:System.Windows.Forms.DataGridView> ou un autre type de contrôle que prend en charge la liaison de données, vous pouvez modifier votre application pour lier le contrôle au résultat d'un objet <xref:System.Data.Objects.ObjectQuery%601>.  
  
 Pour plus d'informations, consultez [Binding Objects to Controls](http://msdn.microsoft.com/fr-fr/2fd34855-929b-4303-a91e-4bb69d958f2b).  
  
 Contrôles de source de données [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclut un contrôle de source de données conçu pour simplifier la liaison de données dans les applications Web [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)].  Pour plus d'informations, voir [Contrôle de source de données Entity Framework](../Topic/EntityDataSource%20Web%20Server%20Control%20Overview.md).  
  
## Autres considérations  
 Les remarques suivantes peuvent s'appliquer lorsque vous effectuez une migration de types spécifiques d'applications vers Entity Framework.  
  
 Applications qui exposent des services de données.  
 Les services Web et les applications basées sur Windows Communication Foundation \(WCF\) exposent les données d'une source de données sous\-jacente en utilisant un format de messagerie de demande\/réponse XML.  [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] prend en charge la sérialisation d'objets entité en utilisant la sérialisation de contrat de données binaire, XML ou WCF.  La sérialisation binaire et la sérialisation WCF prennent tous les deux en charge la sérialisation complète de graphiques d'objets.  Pour plus d'informations, consultez [Building N\-Tier Applications](http://msdn.microsoft.com/fr-fr/9439d2ba-6b5f-44e8-be65-8a442d922cbb).  
  
 Applications qui utilisent des données XML.  
 La sérialisation des objets vous permet de créer des services des données [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Ces services fournissent des données à des applications qui utilisent des données XML, telles que les applications Internet AJAX.  Dans ces cas, envisagez d'utiliser [!INCLUDE[ssAstoria](../../../../../includes/ssastoria-md.md)].  Ces services de données sont basés sur le modèle EDM \(Entity Data Model\) et fournissent un accès dynamique aux données d'entité à l'aide d'actions HTTP REST \(Representational State Transfer\) standard, telles que GET, PUT et POST.  Pour plus d'informations, consultez [WCF Data Services 4.5](../../../../../docs/framework/data/wcf/index.md).  
  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] ne prend pas en charge le type de données XML natif.  Cela signifie que, lorsqu'une entité est mappée à une table avec une colonne XML, la propriété d'entité équivalente de la colonne XML est une chaîne.  Les objets peuvent être déconnectés et sérialisés sous forme de données XML.  Pour plus d'informations, consultez [Serializing Objects](http://msdn.microsoft.com/fr-fr/06c77f9b-5b2e-4c78-b3e3-8c148ba0ea99).  
  
 Si votre application nécessite la possibilité d'interroger des données XML, vous pouvez tout de même tirer parti des avantages des requêtes LINQ en utilisant LINQ to XML.  Pour plus d'informations, consultez [LINQ to XML](../../../../../ocs/visual-basic/programming-guide/concepts/linq/linq-to-xml.md).  
  
 Applications qui gèrent l'état.  
 Les applications Web [!INCLUDE[vstecasp](../../../../../includes/vstecasp-md.md)] doivent fréquemment gérer l'état d'une page Web ou d'une session utilisateur.  Les objets d'une instance de <xref:System.Data.Objects.ObjectContext> peuvent être stockés dans l'état d'affichage client ou dans l'état de session sur le serveur, et être ensuite récupérés et rattachés à un nouveau contexte de l'objet.  Pour plus d'informations, consultez [Attaching and Detaching Objects](http://msdn.microsoft.com/fr-fr/41d5c1ef-1b78-4502-aa10-7e1438d62d23).  
  
## Voir aussi  
 [Points à prendre en considération pour le déploiement](../../../../../docs/framework/data/adonet/ef/deployment-considerations.md)   
 [Terminologie Entity Framework](../../../../../docs/framework/data/adonet/ef/terminology.md)