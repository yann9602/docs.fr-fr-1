---
title: "ref (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ref_CSharpKeyword"
  - "ref"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "paramètres (C#), ref"
  - "ref (mot clé C#)"
ms.assetid: b8a5e59c-907d-4065-b41d-95bf4273c0bd
caps.latest.revision: 32
caps.handback.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ref (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `ref` entraîne le passage d'un argument par référence, et non par valeur.  La conséquence est que toute modification apportée au paramètre dans la méthode appelée est répercutée dans la méthode d'appel.  Par exemple, si l'appelant passe une expression de variable locale ou d'une expression d'accès à un élément de tableau et que la méthode appelée remplace l'objet auquel fait référence le paramètre ref, la variable locale de l'appelant ou l'élément de tableau font désormais référence au nouvel objet.  
  
> [!NOTE]
>  Ne confondez pas le concept de passage par référence avec celui de types de référence.  Les deux concepts ne sont pas identiques.  Un paramètre de méthode peut être modifié par `ref`, qu'il s'agisse d'un type valeur ou d'un type référence.  Il n'y a aucun boxing d'un type valeur lorsqu'il est passé par référence.  
  
 Pour utiliser un paramètre `ref`, la définition de la méthode et la méthode d'appel doivent utiliser explicitement le mot clé `ref`, comme indiqué dans l'exemple suivant.  
  
 [!code-cs[csrefKeywordsMethodParams#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_1.cs)]  
  
 Un argument passé à un paramètre `ref` doit être initialisé avant d'être transmis.  Cette obligation diffère des paramètres `out`, dont les arguments ne doivent pas être explicitement initialisés avant d'être passés.  Pour plus d'informations, consultez [out](../../../csharp/language-reference/keywords/out.md).  
  
 Les membres d'une classe ne peuvent pas avoir de signatures qui diffèrent uniquement par `ref` et `out`.  Une erreur de compilation se produit si la seule différence entre deux membres d'un type est que l'un d'eux a un paramètre refet l'autre un paramètre `out`.  Le code suivant, par exemple, ne se compile pas.  
  
 [!code-cs[csrefKeywordsMethodParams#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_2.cs)]  
  
 Cependant, la surcharge peut avoir lieu quand une méthode a un paramètre `ref` ou `out`, et que l'autre a un paramètre de valeur, comme illustré dans l'exemple suivant.  
  
 [!code-cs[csrefKeywordsMethodParams#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_3.cs)]  
  
 Dans d'autres situations nécessitant une correspondance de signature, comme le masquage ou la substitution, `ref` et `out` font partie de la signature et ne correspondent pas l'un à l'autre.  
  
 Les propriétés ne sont pas des variables.  Ce sont des méthodes et ne peuvent pas être passées aux paramètres `ref`.  
  
 Pour plus d'informations sur le passage de tableaux, consultez [Passage de tableaux à l'aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 Vous ne pouvez pas utiliser les mots clés `ref` et `out` pour les types de méthodes suivants :  
  
-   méthodes Async, que vous définissez à l'aide du modificateur [async](../../../csharp/language-reference/keywords/async.md) ;  
  
-   méthodes Iterator, qui incluent une instruction [yield return](../../../csharp/language-reference/keywords/yield.md) ou `yield break`.  
  
## Exemple  
 Les exemples précédents montrent ce qui se produit lors du passage de types valeur par référence.  Vous pouvez également utiliser le mot clé `ref` pour passer les types référence.  Le passage d'un type référence par référence permet à la méthode appelée de remplacer l'objet dans la méthode appelante à laquelle fait référence le paramètre de référence.  L'emplacement de stockage de l'objet est passé à la méthode comme valeur du paramètre de référence.  Si vous modifiez la valeur de l'emplacement de stockage du paramètre \(pour pointer vers un nouvel objet\), vous modifiez également l'emplacement de stockage auquel fait référence l'appelant.  L'exemple suivant passe une instance d'un type référence en tant que paramètre `ref`.  Pour plus d'informations sur le passage de types référence par valeur et par référence, consultez [Passage de paramètres de type référence](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md).  
  
 [!code-cs[csrefKeywordsMethodParams#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/ref_4.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Passage de paramètres](../../../csharp/programming-guide/classes-and-structs/passing-parameters.md)   
 [Paramètres de méthodes](../../../csharp/language-reference/keywords/method-parameters.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)