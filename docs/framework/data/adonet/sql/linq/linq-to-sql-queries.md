---
title: "Requêtes LINQ to SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8c32ff4040213ce73b78f7ea0f6d56e222d55b25
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="linq-to-sql-queries"></a>Requêtes LINQ to SQL
Vous définissez des requêtes [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en utilisant la même syntaxe que dans [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. La seule différence est que les objets référencés dans vos requêtes sont mappés aux éléments d'une base de données. Pour plus d’informations, consultez [Introduction aux requêtes LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit les requêtes que vous écrivez en requêtes SQL équivalentes et les envoie au serveur pour traitement. Plus spécifiquement, votre application utilise l'API [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour demander l'exécution de la requête. Le fournisseur [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] transforme ensuite la requête en texte SQL et délègue l'exécution au fournisseur ADO. Le fournisseur ADO retourne des résultats de la requête en tant que `DataReader`. Le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournisseur traduit les résultats ADO en une <xref:System.Linq.IQueryable> collection d’objets de l’utilisateur.  
  
> [!NOTE]
>  La plupart des méthodes et opérateurs sur les types intégrés [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] ont des traductions directes en SQL. Ceux que [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] ne peut pas traduire génèrent des exceptions runtime. Pour plus d’informations, consultez [le mappage de Type SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 Le tableau suivant affiche les ressemblances et différences entre les éléments de requête [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
|Élément|Requête LINQ|Requête [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].|  
|----------|----------------|----------------------------------------------------------------------|  
|Type de retour de la variable locale qui contient la requête (pour les requêtes qui retournent des séquences)|`IEnumerable` générique|`IQueryable` générique|  
|Spécification de la source de données|Utilise le `From` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) ou `from` clause (c#)|Identique|  
|Filtrage|Utilise le `Where` / `where` clause|Identique|  
|Regroupement|Utilise le `Group…By` / `groupby` clause|Identique|  
|Sélection (projection)|Utilise le `Select` / `select` clause|Identique|  
|Exécution différée / exécution immédiate|Consultez [Introduction aux requêtes LINQ (c#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Identique|  
|Implémentation de jointures|Utilise le `Join` / `join` clause|Peut utiliser le `Join` / `join` clause, mais utilise plus efficacement la <xref:System.Data.Linq.Mapping.AssociationAttribute> attribut. Pour plus d’informations, consultez [interrogation de relations](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).|  
|Exécution distante / exécution locale||Pour plus d’informations, consultez [à distance Visual Studio. Exécution locale](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md).|  
|Transmission en continu / interrogation mise en cache|Non applicable dans un scénario de mémoire locale||  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction aux requêtes LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [Opérations de requête LINQ de base](~/docs/csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)  
 [Relations des types dans des opérations de requête LINQ](~/docs/csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)  
 [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
