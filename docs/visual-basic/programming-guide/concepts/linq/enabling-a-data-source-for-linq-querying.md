---
title: "L’activation d’une Source de données pour LINQ Querying2 | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c412f0cf-ff0e-4993-ab3d-1b49e23f00f8
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 34bdc4e056d982799eac35eb2398dd3f23f6f351
ms.lasthandoff: 03/13/2017

---
# <a name="enabling-a-data-source-for-linq-querying"></a>Activation d'une source de données pour l'interrogation LINQ
Il existe différentes manières d’étendre [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] pour permettre à toute source de données à rechercher dans la [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] modèle. La source de données peut être une structure de données, un service Web, un système de fichiers ou une base de données, par exemple. Le modèle [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] permet aux clients d'interroger facilement une source de données pour laquelle l'interrogation [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] est activée, car la syntaxe et le modèle de la requête ne changent pas. La manière dont [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] peut être étendu à ces données sources sont les suivantes :  
  
-   L’implémentation de la <xref:System.Collections.Generic.IEnumerable%601>interface dans un type pour activer [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] pour l’interrogation des objets de ce type.</xref:System.Collections.Generic.IEnumerable%601>  
  
-   Création des méthodes d’opérateur de requête standard telles que <xref:System.Linq.Enumerable.Where%2A>et <xref:System.Linq.Enumerable.Select%2A>qui étendent un type, pour activer personnalisé [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] interrogation de ce type.</xref:System.Linq.Enumerable.Select%2A> </xref:System.Linq.Enumerable.Where%2A>  
  
-   Création d’un fournisseur pour votre source de données qui implémente le <xref:System.Linq.IQueryable%601>interface.</xref:System.Linq.IQueryable%601> Un fournisseur qui implémente cette interface reçoit des requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] dans le formulaire des arborescences d'expression, qu'il peut exécuter d'une manière personnalisée, par exemple à distance.  
  
-   Création d’un fournisseur pour votre source de données qui tire parti d’un [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] technologie. Ce type de fournisseur permettrait non seulement l'interrogation, mais également l'insertion, la mise à jour et la suppression d'opérations et le mappage pour des types définis par l'utilisateur.  
  
 Cette rubrique décrit ces options.  
  
## <a name="how-to-enable-linq-querying-of-your-data-source"></a>Comment activer l'interrogation LINQ de votre source de données  
  
### <a name="in-memory-data"></a>Données en mémoire  
 Il existe deux façons, vous pouvez activer [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] interrogation des données en mémoire. Si les données sont d’un type qui implémente <xref:System.Collections.Generic.IEnumerable%601>, vous pouvez interroger les données à l’aide de [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] aux objets.</xref:System.Collections.Generic.IEnumerable%601> S’il est inutile d’activer l’énumération de ce type en implémentant le <xref:System.Collections.Generic.IEnumerable%601>interface, vous pouvez définir [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] standard des méthodes d’opérateur de ce type de requête ou créez [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] méthodes d’opérateur de requête standard qui étendent ce type.</xref:System.Collections.Generic.IEnumerable%601> Les implémentations personnalisées des opérateurs de requête standard doivent utiliser l'exécution différée pour retourner les résultats.  
  
### <a name="remote-data"></a>Données distantes  
 La meilleure option pour activer [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] interrogation d’une source de données distante est d’implémenter la <xref:System.Linq.IQueryable%601>interface.</xref:System.Linq.IQueryable%601> Toutefois, cette méthode diffère de l'extension d'un fournisseur tel que [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] pour une source de données. Aucun modèle de fournisseur pour l’extension existante [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] technologies, telles que [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], en autres types de source de données sont disponibles dans [!INCLUDE[vs_orcas_long](../../../../csharp/misc/includes/vs_orcas_long_md.md)].  
  
## <a name="iqueryable-linq-providers"></a>Fournisseurs LINQ IQueryable  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]les fournisseurs qui implémentent <xref:System.Linq.IQueryable%601>leur complexité peut varier énormément.</xref:System.Linq.IQueryable%601> Cette section décrit les différents niveaux de complexité.  
  
 Un fournisseur `IQueryable` moins complexe peut interagir avec une méthode unique d'un service Web. Ce type de fournisseur est très particulier, car il attend des informations spécifiques dans les requêtes qu'il gère. Il se caractérise par un système de type fermé, exposant peut-être un type de résultat unique. La plupart de l’exécution de la requête est effectuée localement, par exemple en utilisant la <xref:System.Linq.Enumerable>implémentations d’opérateurs de requête standard.</xref:System.Linq.Enumerable> Un fournisseur moins complexe peut examiner une seule expression d'appel de méthode dans l'arborescence d'expression qui représente la requête, et la logique restante de la requête doit être gérée ailleurs.  
  
 Un fournisseur `IQueryable` de complexité moyenne peut cibler une source de données qui possède un langage de requête partiellement expressif. S'il cible un service Web, il peut interagir avec plusieurs méthodes du service Web et sélectionner la méthode d'appel en fonction de la question posée par la requête. Un fournisseur de complexité moyenne aurait un système plus sophistiqué que celui d'un fournisseur simple, qui serait néanmoins un système de type fixe. Par exemple, le fournisseur peut exposer des types qui ont des relations un-à-plusieurs qui peuvent être parcourues, mais il ne fournirait pas de technologie de mappage pour les types définis par l'utilisateur.  
  
 Un fournisseur complexe `IQueryable`, tel que le fournisseur [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], peut convertir les requêtes terminées [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] en un langage de requête expressif, par exemple SQL. Un fournisseur complexe est plus général qu'un fournisseur moins complexe, car il peut gérer une plus grande gamme de questions dans la requête. Il possède également un système de type ouvert et doit donc contenir une infrastructure étendue pour mapper les types définis par l'utilisateur. Développer un fournisseur complexe est une tâche difficile.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.IQueryable%601></xref:System.Linq.IQueryable%601>   
 <xref:System.Collections.Generic.IEnumerable%601></xref:System.Collections.Generic.IEnumerable%601>   
 <xref:System.Linq.Enumerable></xref:System.Linq.Enumerable>   
 [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
