---
title: "Comment&#160;: retourner des sous-ensembles de propri&#233;t&#233;s d&#39;&#233;l&#233;ments dans une requ&#234;te (Guide de programmation&#160;C#) | Microsoft Docs"
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
  - "types anonymes (C#), pour des sous-ensembles de propriétés d'éléments"
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: retourner des sous-ensembles de propri&#233;t&#233;s d&#39;&#233;l&#233;ments dans une requ&#234;te (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Utilisez un type anonyme dans une expression de requête lorsque les deux conditions suivantes s'appliquent :  
  
-   Vous souhaitez renvoyer uniquement certaines des propriétés de chaque élément source.  
  
-   Vous n'êtes pas obligé de stocker les résultats de la requête hors de la portée de la méthode dans laquelle s'exécute la requête.  
  
 Si vous souhaitez uniquement retourner une propriété ou un champ de chaque élément source, il vous suffit d'utiliser l'opérateur point dans la clause `select`.  Par exemple, pour retourner uniquement l'`ID` de chaque `student`, écrivez la clause `select` comme suit :  
  
```  
select student.ID;  
```  
  
## Exemple  
 L'exemple suivant indique comment utiliser un type anonyme pour retourner uniquement un sous\-ensemble des propriétés de chaque élément source qui correspond à la condition spécifiée.  
  
 [!code-cs[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 Notez que le type anonyme utilise les noms de l'élément source pour ses propriétés si aucun nom n'est spécifié.  Pour attribuer de nouveaux noms aux propriétés dans le type anonyme, écrivez l'instruction `select` comme suit :  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 Si vous essayez cette procédure dans l'exemple précédent, l'instruction `Console.WriteLine` doit également être modifiée :  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## Compilation du code  
  
-   Pour exécuter ce code, copiez et collez la classe dans un projet d'application console Visual C\# qui a été créé dans [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)].  Par défaut, ce projet cible la version 3.5 du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] et comportera une référence à System.Core.dll et une directive `using` pour System.Linq.  Si une ou plusieurs de ces spécifications sont absentes du projet, vous pouvez les ajouter manuellement.  Pour plus d'informations, consultez [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)