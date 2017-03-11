---
title: "Type Relationships in LINQ Query Operations (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "inferring type information [LINQ in C#]"
  - "data sources [LINQ in C#], type relationships"
  - "queries [LINQ in C#], type relationships"
  - "relationships [LINQ in C#]"
  - "type relationships [LINQ in C#]"
  - "variable relationships [LINQ in C#]"
  - "type information inferred [LINQ in C#]"
  - "data transformations [LINQ in C#]"
  - "LINQ [C#], type relationships"
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
caps.latest.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# Type Relationships in LINQ Query Operations (C#)
Pour écrire des requêtes de manière efficace, vous devez comprendre comment les types des variables dans une opération de requête complète sont tous liés les uns aux autres.  Si vous comprenez ces relations, vous comprendrez plus facilement les exemples de code et exemples [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] dans la documentation.  En outre, vous comprendrez ce qui se passe en arrière\-plan lorsque des variables sont implicitement typées à l'aide de `var`.  
  
 Les opérations de requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] sont fortement typées dans la source de données, dans la requête elle\-même et dans l'exécution de la requête.  Le type des variables dans la requête doit être compatible avec le type des éléments dans la source de données, ainsi qu'avec le type de la variable d'itération dans l'instruction `foreach`.  Ce typage fort garantit l'interception des erreurs de type au moment de la compilation lorsqu'elles peuvent être corrigées avant que les utilisateurs ne les rencontrent.  
  
 Pour illustrer ces relations des types, la plupart des exemples qui suivent utilisent le type explicite pour toutes les variables.  Le dernier exemple indique comment les mêmes principes s'appliquent, même lorsque vous utilisez des types implicites à l'aide de [var](../../../../csharp/language-reference/keywords/var.md).  
  
## Les requêtes qui ne transforment pas les données source  
 L'illustration suivante présente une opération de requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] to Objects qui n'effectue pas de transformation des données.  La source contient une séquence de chaînes et le résultat de la requête est également une séquence de chaînes.  
  
 ![Relation entre les types de données dans une requête LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq-flow1.png "LINQ\_flow1")  
  
1.  L'argument de type de la source de données détermine le type de la variable de portée.  
  
2.  Le type de l'objet sélectionné détermine le type de la variable de requête.  Ici, `name` est une chaîne.  Par conséquent, la variable de requête est un `IEnumerable`\<chaîne\>.  
  
3.  La variable de requête est itérée au sein de l'instruction `foreach`.  Étant donné que la variable de requête est une séquence de chaînes, la variable d'itération est également une chaîne.  
  
## Les requêtes qui transforment les données source  
 L'illustration suivante présente une opération de requête [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)] qui effectue une transformation simple des données.  La requête prend une séquence d'objets `Customer` comme entrée et sélectionne uniquement la propriété `Name` dans le résultat.  Étant donné que `Name` est une chaîne, la requête produit une séquence de chaînes comme sortie.  
  
 ![Requête qui transforme le type de données](../../../../csharp/programming-guide/concepts/linq/media/linq-flow2.png "LINQ\_flow2")  
  
1.  L'argument de type de la source de données détermine le type de la variable de portée.  
  
2.  L'instruction `select` retourne la propriété `Name` au lieu de l'objet `Customer` complet.  Étant donné que `Name` est une chaîne, l'argument de type de `custNameQuery` est `string`, et non `Customer`.  
  
3.  Étant donné que `custNameQuery` est une séquence de chaînes, la variable d'itération de la boucle `foreach` doit également être une `string`.  
  
 L'illustration suivante présente une transformation sensiblement plus complexe.  L'instruction `select` retourne un type anonyme qui capture seulement deux membres de l'objet `Customer` d'origine.  
  
 ![Requête qui transforme le type de données](../../../../csharp/programming-guide/concepts/linq/media/linq-flow3.png "LINQ\_flow3")  
  
1.  L'argument de type de la source de données est toujours le type de la variable de portée dans la requête.  
  
2.  Étant donné que l'instruction `select` produit un type anonyme, la variable de requête doit être implicitement typée à l'aide de `var`.  
  
3.  Étant donné que le type de la variable de requête est implicite, la variable d'itération dans la boucle `foreach` doit également être implicite.  
  
## Laisser le compilateur déduire les informations de type  
 Même si vous devez comprendre les relations des types dans une opération de requête, vous avez la possibilité de laisser le compilateur faire tout le travail pour vous.  Le mot clé [var](../../../../csharp/language-reference/keywords/var.md) peut être utilisé pour toute variable locale dans une opération de requête.  L'illustration suivante équivaut à l'exemple numéro 2 qui a été abordé précédemment.  Toutefois, le compilateur fournit le type fort pour chaque variable de l'opération de requête.  
  
 ![Flux de type avec typage implicite](../../../../csharp/programming-guide/concepts/linq/media/linq-flow4.png "LINQ\_flow4")  
  
 Pour plus d'informations sur `var`, consultez [Variables locales implicitement typées](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## Voir aussi  
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Type Relationships in Query Operations \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)