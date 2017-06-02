---
title: "Requ&#234;tes LINQ to SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Requ&#234;tes LINQ to SQL
Vous définissez des requêtes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en utilisant la même syntaxe que dans [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  La seule différence est que les objets référencés dans vos requêtes sont mappés aux éléments d'une base de données.  Pour plus d'informations, consultez [Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les requêtes que vous écrivez en requêtes SQL équivalentes et les envoie au serveur pour traitement. Plus spécifiquement, votre application utilise l'API [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour demander l'exécution de la requête.  Le fournisseur [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] transforme ensuite la requête en texte SQL et délègue l'exécution au fournisseur ADO. Le fournisseur ADO retourne des résultats de la requête en tant que `DataReader`.  Le fournisseur [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les résultats ADO en une collection <xref:System.Linq.IQueryable> d'objets utilisateur.  
  
> [!NOTE]
>  La plupart des méthodes et opérateurs sur les types intégrés [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] ont des traductions directes en SQL.  Ceux que [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] ne peut pas traduire génèrent des exceptions runtime.  Pour plus d'informations, consultez [Mappage de type SQL\-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 Le tableau suivant affiche les ressemblances et différences entre les éléments de requête [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
|Élément|Requête LINQ|Requête [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|-------------|------------------|-------------------------------------------------------------------------|  
|Type de retour de la variable locale qui contient la requête \(pour les requêtes qui retournent des séquences\)|`IEnumerable` générique|`IQueryable` générique|  
|Spécification de la source de données|Utilise la clause `From` \([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]\) ou la clause `from` \(C\#\)|Identique|  
|Filtrage|Utilise la clause `Where`\/`where`|Identique|  
|Regroupement|Utilise la clause `Group…By`\/`groupby`|Identique|  
|Sélection \(projection\)|Utilise la clause `Select`\/`select`|Identique|  
|Exécution différée \/ exécution immédiate|Consultez [Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)|Identique|  
|Implémentation de jointures|Utilise la clause `Join`\/`join`|Peut utiliser la clause `Join`\/`join`, mais utilise plus efficacement l'attribut <xref:System.Data.Linq.Mapping.AssociationAttribute>.  Pour plus d'informations, consultez [Interrogation de relations](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).|  
|Exécution distante \/ exécution locale||Pour plus d'informations, consultez [Comparaison entre une exécution locale et une exécution distante](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md).|  
|Transmission en continu \/ interrogation mise en cache|Non applicable dans un scénario de mémoire locale||  
  
## Voir aussi  
 [Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md)   
 [Basic LINQ Query Operations](../Topic/Basic%20LINQ%20Query%20Operations%20\(C%23\).md)   
 [Type Relationships in LINQ Query Operations](../Topic/Type%20Relationships%20in%20LINQ%20Query%20Operations%20\(C%23\).md)   
 [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)