---
title: "Fonctionnalit&#233;s non prises en charge | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Fonctionnalit&#233;s non prises en charge
Dans LINQ to SQL, les fonctionnalités SQL suivantes ne peuvent pas être exposées via la traduction de constructions du Common Language Runtime \(CLR\) et .NET Framework existantes :  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     Bien que `LIKE` ne soit pas prise en charge par le biais de la traduction directe, il existe des fonctionnalités similaires dans la classe <xref:System.Data.Linq.SqlClient.SqlMethods>.  Pour plus d'informations, consultez [M:System.Data.Linq.SqlClient.SqlMethods.Like\(System.String,System.String](assetId:///M:System.Data.Linq.SqlClient.SqlMethods.Like(System.String,System.String?qualifyHint=True&autoUpgrade=True).  
  
-   `DATEDIFF`  
  
     LINQ to SQL a une prise en charge limitée de `DATEDIFF`.  Il existe des fonctionnalités similaires dans la classe [SqlMethods](assetId:///T:System.Data.Linq.SqlClient.SqlMethods?qualifyHint=False&autoUpgrade=True).  
  
-   `ROUND`  
  
     LINQ to SQL a une prise en charge limitée de `ROUND`.  Pour plus d'informations, consultez [Méthodes System.Math](../Topic/System.Math%20Methods.md).  
  
## Voir aussi  
 [Fonctions et types de données](../Topic/Data%20Types%20and%20Functions.md)