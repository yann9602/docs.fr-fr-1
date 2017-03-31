---
title: "Activation d’une source de données pour l’interrogation LINQ1 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: d2ef04a5-31a6-45cb-af9a-a5ce7732662c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a5eaa6472c5fd7942f345dc5b4401b85c33504c9
ms.lasthandoff: 03/13/2017

---
# <a name="enabling-a-data-source-for-linq-querying"></a>Activation d'une source de données pour l'interrogation LINQ
Il y a différentes méthodes pour étendre [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] pour permettre l’interrogation de toute source de données dans le modèle [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]. La source de données peut être une structure de données, un service Web, un système de fichiers ou une base de données, par exemple. Le modèle [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] permet aux clients d'interroger facilement une source de données pour laquelle l'interrogation [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] est activée, car la syntaxe et le modèle de la requête ne changent pas. Il existe différentes manières d’étendre [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] à ces sources de données, dont les suivantes :  
  
-   Implémentation de l’interface <xref:System.Collections.Generic.IEnumerable%601> dans un type pour activer l’interrogation [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] to Objects de ce type.  
  
-   Création de méthodes d’opérateur de requête standard telles que <xref:System.Linq.Enumerable.Where%2A> et <xref:System.Linq.Enumerable.Select%2A> qui étendent un type, pour activer l’interrogation [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] personnalisée de ce type.  
  
-   Création d’un fournisseur pour votre source de données qui implémente l’interface <xref:System.Linq.IQueryable%601>. Un fournisseur qui implémente cette interface reçoit des requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] dans le formulaire des arborescences d'expression, qu'il peut exécuter d'une manière personnalisée, par exemple à distance.  
  
-   Création d’un fournisseur pour votre source de données qui exploite une technologie [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] existante. Ce type de fournisseur permettrait non seulement l'interrogation, mais également l'insertion, la mise à jour et la suppression d'opérations et le mappage pour des types définis par l'utilisateur.  
  
 Cette rubrique décrit ces options.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Comment activer l'interrogation LINQ de votre source de données  
  
### <a name="in-memory-data"></a>Données en mémoire  
 Vous pouvez activer l’interrogation [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] des données en mémoire de deux manières. Si les données sont d’un type qui implémente <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez interroger les données en utilisant [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] to Objects. S’il est inutile d’activer l’énumération de ce type par l’implémentation de l’interface <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez définir des méthodes d’opérateur de requête standard [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] dans ce type ou créer des méthodes d’opérateur de requête standard [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] qui étendent ce type. Les implémentations personnalisées des opérateurs de requête standard doivent utiliser l'exécution différée pour retourner les résultats.  
  
### <a name="remote-data"></a>Données distantes  
 La meilleure manière d’activer l’interrogation [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] d’une source de données distante est d’implémenter l’interface <xref:System.Linq.IQueryable%601>. Toutefois, cette méthode diffère de l'extension d'un fournisseur tel que [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] pour une source de données. Aucun modèle de fournisseur pour l’extension des technologies [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] existantes (telles que [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]), à d’autres types de source de données n’est disponible dans [!INCLUDE[vs_orcas_long](../../../../csharp/misc/includes/vs_orcas_long_md.md)].  
  
## <a name="iqueryable-linq-providers"></a>Fournisseurs LINQ IQueryable  
 La complexité des fournisseurs [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] qui implémentent <xref:System.Linq.IQueryable%601> peut varier énormément. Cette section décrit les différents niveaux de complexité.  
  
 Un fournisseur `IQueryable` moins complexe peut interagir avec une méthode unique d'un service Web. Ce type de fournisseur est très particulier, car il attend des informations spécifiques dans les requêtes qu'il gère. Il se caractérise par un système de type fermé, exposant peut-être un type de résultat unique. La plus grande part de l’exécution de la requête est effectuée localement, par exemple à l’aide des implémentations <xref:System.Linq.Enumerable> des opérateurs de requête standard. Un fournisseur moins complexe peut examiner une seule expression d'appel de méthode dans l'arborescence d'expression qui représente la requête, et la logique restante de la requête doit être gérée ailleurs.  
  
 Un fournisseur `IQueryable` de complexité moyenne peut cibler une source de données qui possède un langage de requête partiellement expressif. S'il cible un service Web, il peut interagir avec plusieurs méthodes du service Web et sélectionner la méthode d'appel en fonction de la question posée par la requête. Un fournisseur de complexité moyenne aurait un système plus sophistiqué que celui d'un fournisseur simple, qui serait néanmoins un système de type fixe. Par exemple, le fournisseur peut exposer des types qui ont des relations un-à-plusieurs qui peuvent être parcourues, mais il ne fournirait pas de technologie de mappage pour les types définis par l'utilisateur.  
  
 Un fournisseur complexe `IQueryable`, tel que le fournisseur [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], peut convertir les requêtes terminées [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] en un langage de requête expressif, par exemple SQL. Un fournisseur complexe est plus général qu'un fournisseur moins complexe, car il peut gérer une plus grande gamme de questions dans la requête. Il possède également un système de type ouvert et doit donc contenir une infrastructure étendue pour mapper les types définis par l'utilisateur. Développer un fournisseur complexe est une tâche difficile.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.IQueryable%601>   
 <xref:System.Collections.Generic.IEnumerable%601>   
 <xref:System.Linq.Enumerable>   
 [Vue d’ensemble des opérateurs de requête standard (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)
