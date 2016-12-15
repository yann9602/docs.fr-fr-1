---
title: "LINQ and Generic Types (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "LINQ [C#], generic types"
  - "generic types [LINQ]"
  - "generics [LINQ]"
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
caps.latest.revision: 18
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# LINQ and Generic Types (C#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] sont basées sur des types génériques introduits dans la version 2.0 du [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)].  Il n'est pas nécessaire de connaître parfaitement les génériques pour commencer à écrire des requêtes.  Toutefois, il est important de comprendre deux concepts de base :  
  
1.  Lorsque vous créez une instance d'une classe de collection générique telle que <xref:System.Collections.Generic.List%601>, vous remplacez le « T » par le type des objets contenus dans la liste.  Par exemple, une liste de chaînes est exprimée sous la forme `List<string>` et une liste d'objets `Customer` sous la forme `List<Customer>`.  Une liste générique est fortement typée et offre de nombreux avantages par rapport aux collections qui stockent leurs éléments en tant que <xref:System.Object>.  Si vous essayez d'ajouter un `Customer` à un `List<string>`, vous obtiendrez une erreur à la compilation.  Vous pouvez facilement utiliser des collections génériques car il n'est pas nécessaire d'effectuer un cast de type au moment de l'exécution.  
  
2.  <xref:System.Collections.Generic.IEnumerable%601> est l'interface qui permet l'énumération des classes de collections génériques à l'aide de l'instruction `foreach`.  Les classes de collections génériques prennent en charge <xref:System.Collections.Generic.IEnumerable%601> et les classes de collections non génériques, telles que <xref:System.Collections.ArrayList>, prennent en charge <xref:System.Collections.IEnumerable>.  
  
 Pour plus d'informations sur les génériques, consultez [Génériques](../../../../csharp/programming-guide/generics/index.md).  
  
## Variables IEnumerable \<T\> dans les requêtes LINQ  
 Les variables de requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] sont typées comme <xref:System.Collections.Generic.IEnumerable%601> ou de type dérivé comme <xref:System.Linq.IQueryable%601>.  Lorsque vous avez une variable de requête typée comme `IEnumerable<Customer>`, cela signifie simplement que la requête, lorsqu'elle est exécutée, génère une séquence de zéro objets `Customer` ou plus.  
  
 [!code-cs[csLINQGettingStarted#34](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_1.cs)]  
  
 Pour plus d'informations, consultez [Type Relationships in LINQ Query Operations](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## Gestion des déclarations de type générique par le compilateur  
 Si vous le souhaitez, vous pouvez éviter d'utiliser la syntaxe générique à l'aide du mot clé [var](../../../../csharp/language-reference/keywords/var.md).  Le mot clé `var` indique au compilateur de déduire le type d'une variable de requête de la source de données spécifiée dans la clause `from`.  L'exemple suivant génère le même code compilé que dans l'exemple précédent :  
  
 [!code-cs[csLINQGettingStarted#35](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/linq-and-generic-types_2.cs)]  
  
 Le mot clé `var` est utile lorsque le type de la variable est évident ou lorsqu'il n'est pas particulièrement important de spécifier explicitement les types génériques imbriqués tels que ceux générés par les requêtes de groupe.  En général, si vous utilisez `var`, vous devez savoir que cela peut compliquer la lecture de votre code.  Pour plus d'informations, consultez [Variables locales implicitement typées](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## Voir aussi  
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Génériques](../../../../csharp/programming-guide/generics/index.md)