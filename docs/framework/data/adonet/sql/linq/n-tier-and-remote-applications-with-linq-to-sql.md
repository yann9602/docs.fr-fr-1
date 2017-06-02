---
title: "Applications multicouches et distantes avec LINQ to SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Applications multicouches et distantes avec LINQ to SQL
Vous pouvez créer des applications multicouches qui utilisent [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  En général, le contexte de données [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], les classes d'entité et la logique de construction de requête sont situés sur la couche intermédiaire nommée couche Data Access.  La logique métier et toutes les données non persistantes peuvent être implémentées entièrement dans des classes et des méthodes partielles et le contexte de données, ou ils peuvent être implémentés dans des classes distinctes.  
  
 Le niveau client ou la couche Présentation appelle des méthodes sur l'interface distante de la couche intermédiaire, et la couche Data Access sur cette couche exécutera des requêtes ou des procédures stockées qui sont mappées aux méthodes <xref:System.Data.Linq.DataContext>.  La couche intermédiaire retourne les données aux clients généralement sous la forme de représentations XML d'entités ou objets proxy.  
  
 Sur la couche intermédiaire, les entités sont créées par le contexte de données, qui suit leur état et gère le chargement et la soumission différés des modifications à partir de et vers la base de données.  Ces entités sont "attachées" au `DataContext`.  Toutefois, après que les entités ont été envoyées vers une autre couche par le biais de la sérialisation, elles deviennent détachées, ce qui signifie que `DataContext` ne suit plus leur état.  Les entités que le client renvoie pour les mises à jour doivent être préalablement rattachées au contexte de données pour que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] puisse soumettre les modifications à la base de données.  Le client est chargé de renvoyer les valeurs et\/ou horodatages d'origine à la couche intermédiaire si ceux\-ci sont requis pour les contrôles d'accès concurrentiel optimiste.  
  
 Dans les applications ASP.NET, <xref:System.Web.UI.WebControls.LinqDataSource> gère la plus grande part de cette complexité.  Pour plus d'informations, consultez [NIB: LinqDataSource Web Server Control Overview](http://msdn.microsoft.com/fr-fr/104cfc3f-7385-47d3-8a51-830dfa791136).  
  
## Ressources supplémentaires  
 Pour plus d'informations sur l'implémentation des applications multicouches qui utilisent [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], consultez les rubriques suivantes :  
  
-   [Applications multicouches LINQ to SQL avec ASP.NET](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [Applications multicouches LINQ to SQL avec les services Web](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [LINQ to SQL avec des applications client\-serveur fortement couplées](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [Implémentation de la logique métier multicouche](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [Récupération de données et opérations CUD dans les applications multicouches \(LINQ to SQL\)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 Pour plus d'informations sur les applications multicouches qui utilisent les groupes de données ADO.NET, consultez [Utilisation de groupes de données dans des applications multicouches](../Topic/Work%20with%20datasets%20in%20n-tier%20applications.md).  
  
## Voir aussi  
 [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)