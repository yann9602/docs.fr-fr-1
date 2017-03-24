---
title: "Comment : utiliser des arborescences d’Expression pour générer des requêtes dynamiques (Visual Basic) | Documents Microsoft"
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
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
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
ms.openlocfilehash: 8d69be78a9f3568535dffe54e21af80c6eb12f70
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a>Comment : utiliser des arborescences d’Expression pour générer des requêtes dynamiques (Visual Basic)
Dans LINQ, les arborescences d’expression sont utilisés pour représenter des requêtes structurées qui cible des sources de données qui implémentent <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> Par exemple, le fournisseur LINQ implémente la <xref:System.Linq.IQueryable%601>interface pour l’interrogation de données relationnelles.</xref:System.Linq.IQueryable%601> Le compilateur Visual Basic compile les requêtes qui ciblent des sources dans le code qui génère une arborescence d’expression lors de l’exécution. Le fournisseur de requête peut ensuite parcourir la structure de données arborescente expression et traduire dans un langage de requête approprié pour la source de données.  
  
 Arborescences d’expression sont également utilisées dans LINQ pour représenter des expressions lambda qui sont associées aux variables de type <xref:System.Linq.Expressions.Expression%601>.</xref:System.Linq.Expressions.Expression%601>  
  
 Cette rubrique décrit comment utiliser des arborescences d’expression pour créer des requêtes LINQ dynamiques. Les requêtes dynamiques sont utiles lorsque les caractéristiques d’une requête ne sont pas connus au moment de la compilation. Par exemple, une application peut fournir une interface utilisateur qui permet aux utilisateurs de spécifier un ou plusieurs prédicats pour filtrer les données. Pour utiliser LINQ pour interroger, ce type d’application doit utiliser les arborescences d’expression pour créer la requête LINQ au runtime.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser des arborescences d’expression pour construire une requête sur un `IQueryable` de source de données et de l’exécuter. Le code génère une arborescence d’expression pour représenter la requête suivante :  
  
 `companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`  
  
 Les méthodes de fabrique dans la <xref:System.Linq.Expressions>espace de noms sont utilisés pour créer des arborescences d’expression qui représentent les expressions composant la requête globale.</xref:System.Linq.Expressions> Les expressions qui représentent des appels aux méthodes d’opérateur de requête standard font référence à la <xref:System.Linq.Queryable>des implémentations de ces méthodes.</xref:System.Linq.Queryable> La dernière arborescence d’expression est passée à la <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29>implémentation du fournisseur de la `IQueryable` source de données pour créer une requête exécutable de type `IQueryable`.</xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> Les résultats sont obtenus par énumération de cette variable de requête.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Ce code utilise un nombre fixe d’expressions dans le prédicat qui est transmis à la `Queryable.Where` (méthode). Toutefois, vous pouvez écrire une application qui combine un nombre variable d’expressions de prédicat qui dépend de l’entrée d’utilisateur. Vous pouvez également varier les opérateurs de requête standard qui sont appelées dans la requête, en fonction de l’entrée de l’utilisateur.  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Créer un nouveau **Application Console** projet.  
  
-   Ajoutez une référence à System.Core.dll si elle n’est pas déjà référencée.  
  
-   Inclure l’espace de noms System.Linq.Expressions.  
  
-   Copiez le code de l’exemple et collez-le dans le `Main` `Sub` procédure.  
  
## <a name="see-also"></a>Voir aussi  
 [Arborescences d’expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)   
 [Comment : exécuter des arborescences d’Expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
