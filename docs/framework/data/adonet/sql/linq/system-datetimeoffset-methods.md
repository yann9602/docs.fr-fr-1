---
title: "M&#233;thodes System.DateTimeOffset | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# M&#233;thodes System.DateTimeOffset
Une fois mappés dans le modèle objet ou le fichier de mappage externe, LINQ to SQL vous permet d'appeler la plupart des méthodes, opérateurs et propriétés <xref:System.DateTimeOffset?displayProperty=fullName> à partir des requêtes LINQ to SQL.  
  
 Les seules méthodes non prises en charge sont celles héritées de <xref:System.Object?displayProperty=fullName> qui n'ont pas de sens dans le contexte des requêtes LINQ to SQL, telles que `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.  Ces méthodes ne sont pas prises en charge car LINQ to SQL ne peut pas les traduire à des fins d'exécution sur SQL Server.  
  
> [!NOTE]
>  La structure <xref:System.DateTimeOffset?displayProperty=fullName> CLR \(Common Language Runtime\), ainsi que la capacité à la mapper à une colonne `DATETIMEOFFSET` SQL à l'aide de LINQ to SQL, requiert le .NET Framework 3.5 SP1 ou version ultérieure.  La colonne `DATETIMEOFFSET` SQL est uniquement disponible à partir de Microsoft SQL Server 2008.  
  
## Méthodes de date et d'heure SQLMethods  
 Outre les méthodes proposées par la structure <xref:System.DateTimeOffset>, LINQ to SQL fournit également celles répertoriées dans le tableau suivant à partir de la classe <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=fullName> pour l'utilisation des données de date et d'heure.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## Voir aussi  
 [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)   
 [Création du modèle objet](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)   
 [Mappage de type SQL\-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)