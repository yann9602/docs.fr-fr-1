---
title: "Guide pratique pour utiliser des arborescences d’expressions dans le but de générer des requêtes dynamiques (C#) | Microsoft Docs"
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
ms.assetid: 52cd44dd-a3ec-441e-b93a-4eca388119c7
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
ms.openlocfilehash: 7de999848870de80996f308affde088088e32e52
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-c"></a>Guide pratique pour utiliser des arborescences d’expressions dans le but de générer des requêtes dynamiques (C#)
Dans LINQ, les arborescences d’expressions sont utilisées pour représenter des requêtes structurées qui ciblent des sources de données qui implémentent <xref:System.Linq.IQueryable%601>. Par exemple, le fournisseur LINQ implémente l’interface <xref:System.Linq.IQueryable%601> pour interroger des données relationnelles. Le compilateur C# compile les requêtes qui ciblent de telles sources de données dans du code qui génère une arborescence d’expressions lors de l’exécution. Le fournisseur de requêtes peut ensuite parcourir la structure de données de l’arborescence d’expressions et la traduire en un langage de requête qui convienne à la source de données.  
  
 Les arborescences d’expressions sont également utilisées dans LINQ pour représenter des expressions lambda qui sont associées aux variables de type <xref:System.Linq.Expressions.Expression%601>.  
  
 Cette rubrique explique comment utiliser des arborescences d’expressions pour créer des requêtes LINQ dynamiques. Les requêtes dynamiques sont utiles lorsque les caractéristiques d’une requête ne sont pas connues au moment de la compilation. Par exemple, une application peut fournir une interface utilisateur qui permet aux utilisateurs de spécifier un ou plusieurs prédicats pour filtrer des données. Si vous souhaitez utiliser LINQ pour interroger des données, ce type d’application doit utiliser des arborescences d’expressions pour créer la requête LINQ au moment de l’exécution.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser des arborescences d’expressions pour construire une requête et l’exécuter sur une source de données `IQueryable`. Le code génère une arborescence d’expressions pour représenter la requête suivante :  
  
 `companies.Where(company => (company.ToLower() == "coho winery" || company.Length > 16)).OrderBy(company => company)`  
  
 Les méthodes de fabrique de l’espace de noms <xref:System.Linq.Expressions> sont utilisées pour créer des arborescences d’expressions qui représentent les expressions qui composent l’ensemble de la requête. Les expressions qui représentent des appels aux méthodes d’opérateur de requête standard référencent les implémentations <xref:System.Linq.Queryable> de ces méthodes. La dernière arborescence d’expressions est passée à l’implémentation <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> du fournisseur de la source de données `IQueryable` pour créer une requête exécutable de type `IQueryable`. Les résultats sont obtenus par l’énumération de cette variable de requête.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Ce code utilise un nombre fixe d’expressions dans le prédicat qui est passé à la méthode `Queryable.Where`. Toutefois, vous pouvez écrire une application qui combine un nombre variable d’expressions de prédicat dépendant des entrées utilisateur. Vous pouvez également varier les opérateurs de requête standard qui sont appelés dans la requête, en fonction des entrées utilisateur.  
  
## <a name="compiling-the-code"></a>Compilation du code  
  
-   Créez un projet **Application console**.  
  
-   Ajoutez une référence à System.Core.dll, si cette référence n’existe pas encore.  
  
-   Incluez l’espace de noms System.Linq.Expressions.  
  
-   Copiez le code de l’exemple et collez-le dans la méthode `Main`.  
  
## <a name="see-also"></a>Voir aussi  
 [Arborescences d’expressions (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)   
 [Guide pratique pour exécuter des arborescences d’expressions (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)   
 [Guide pratique pour spécifier dynamiquement des filtres de prédicat au moment de l’exécution](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
