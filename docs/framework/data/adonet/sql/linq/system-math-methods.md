---
title: "M&#233;thodes System.Math | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0f299521-6f41-4720-bd70-67c93fc50948
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# M&#233;thodes System.Math
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne prend pas en charge les méthodes <xref:System.Math> suivantes.  
  
-   <xref:System.Math.DivRem%28System.Int32%2CSystem.Int32%2CSystem.Int32%40%29?displayProperty=fullName>  
  
-   <xref:System.Math.DivRem%28System.Int64%2CSystem.Int64%2CSystem.Int64%40%29?displayProperty=fullName>  
  
-   <xref:System.Math.IEEERemainder%28System.Double%2CSystem.Double%29?displayProperty=fullName>  
  
## Différences par rapport à .NET  
 Le .NET Framework présente une sémantique d'arrondi différente de SQL Server.  La méthode <xref:System.Math.Round%2A> du .NET Framework utilise l'*arrondi bancaire*, dans lequel les nombres qui se terminent par « ,5 » sont arrondis au chiffre pair le plus proche et non au chiffre supérieur suivant.  Par exemple, 2,5 est arrondi à 2 et 3,5 à 4.  Cette technique permet d'éviter les écarts systématiques vers des valeurs supérieures dans les transactions de données importantes.  
  
 Dans SQL, la fonction `ROUND` arrondit toujours vers le chiffre supérieur.  Ainsi, 2,5 est arrondi à 3 \(contre 2 dans le .NET Framework\).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] passe par la sémantique `ROUND` de SQL et ne tente pas d'implémenter l'arrondi bancaire.  
  
## Voir aussi  
 [Fonctions et types de données](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)