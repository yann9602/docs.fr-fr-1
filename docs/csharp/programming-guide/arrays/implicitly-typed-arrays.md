---
title: "Tableaux implicitement typ&#233;s (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "tableaux (C#), implicitement typés"
  - "langage C#, tableaux implicitement typés"
  - "tableaux implicitement typés (C#)"
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# Tableaux implicitement typ&#233;s (Guide de programmation&#160;C#)
Vous pouvez créer un tableau implicitement typé dans lequel le type de l'instance de tableau est déduit des éléments spécifiés dans l'initialiseur de tableau.  Les règles de toute variable implicitement typée s'appliquent également aux tableaux implicitement typés.  Pour plus d'informations, consultez [Variables locales implicitement typées](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 Les tableaux implicitement typés sont généralement utilisés dans les expressions de requête avec les types anonymes et les initialiseurs d'objets et de collection.  
  
 Les exemples suivants indiquent comment créer un tableau implicitement typé :  
  
 [!code-cs[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#37)]  
  
 Dans l'exemple précédent, notez qu'avec des tableaux implicitement typés, aucun crochet n'est utilisé à gauche de l'instruction d'initialisation.  Notez également que les tableaux en escalier sont initialisés en utilisant `new []`, à l'instar des tableaux unidimensionnels.  
  
## Tableaux implicitement typés dans les initialiseurs d'objets  
 Lorsque vous créez un type anonyme qui contient un tableau, le tableau doit être implicitement typé dans l'initialiseur d'objet du type.  Dans l'exemple suivant, `contacts` est un tableau implicitement typé de types anonymes dont chacun contient un tableau nommé `PhoneNumbers`.  Notez que le mot clé `var` n'est pas utilisé à l'intérieur des initialiseurs d'objets.  
  
 [!code-cs[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#38)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Variables locales implicitement typées](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Initialiseurs d'objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)   
 [var](../../../csharp/language-reference/keywords/var.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)