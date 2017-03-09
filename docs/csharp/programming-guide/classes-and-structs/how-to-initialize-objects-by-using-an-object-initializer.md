---
title: "Comment&#160;: initialiser des objets &#224; l&#39;aide d&#39;un initialiseur d&#39;objet (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "initialiseurs d'objets (C#), comment utiliser"
  - "objets (C#), initialiser"
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# Comment&#160;: initialiser des objets &#224; l&#39;aide d&#39;un initialiseur d&#39;objet (Guide de programmation&#160;C#)
Vous pouvez utiliser des initialiseurs d'objets pour initialiser des objets de type de façon sans appeler explicitement un constructeur pour le type.  
  
 Les exemples suivants indiquent comment utiliser des initialiseurs d'objets avec les objets nommés.  Les processus de compilateur objet des initialiseurs en accédant d'abord au constructeur d'instance par défaut et en traitant ensuite les initialisations membres.  Par conséquent, si le constructeur par défaut est déclaré `private` dans la classe, les initialiseurs d'objets qui requièrent un accès public échoueront.  
  
 Vous devez utiliser un initialiseur d'objet si vous définissez un type anonyme.  Pour plus d’informations, consultez [Comment : retourner des sous\-ensembles de propriétés d'éléments dans une requête](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).  
  
## Exemple  
 L'exemple suivant indique comment initialiser un nouveau type `StudentName` à l'aide des initialiseurs d'objets.  
  
 [!code-cs[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#35)]  
  
## Exemple  
 L'exemple suivant indique comment initialiser une collection de types `StudentName` en utilisant un initialiseur de collection.  Notez qu'un initialiseur de collection est une série d'initialiseurs d'objets séparés par des virgules.  
  
 [!code-cs[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#36)]  
  
## Compilation du code  
 Pour exécuter ce code, copiez et collez la classe dans un projet d'application console Visual C\# qui a été créé dans [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)].  Pour plus d’informations, consultez [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Initialiseurs d'objets et de collections](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)