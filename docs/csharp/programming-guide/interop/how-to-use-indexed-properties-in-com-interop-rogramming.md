---
title: "Comment&#160;: utiliser des propri&#233;t&#233;s index&#233;es dans la programmation COM&#160;Interop (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "propriétés indexées (C#)"
  - "programmation Office (C#), propriétés indexées"
  - "propriétés (C#), indexées"
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# Comment&#160;: utiliser des propri&#233;t&#233;s index&#233;es dans la programmation COM&#160;Interop (Guide de programmation&#160;C#)
Les *propriétés indexées* améliorent la façon dont les propriétés COM qui ont des paramètres sont consommées dans la programmation en C\#.  Les propriétés indexées opèrent avec d'autres fonctionnalités introduites dans Visual C\# 2010, telles que les [arguments nommés et optionnels](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), un nouveau type \([dynamique](../../../csharp/language-reference/keywords/dynamic.md)\) et des [informations de type incorporées](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md), pour améliorer la programmation Microsoft Office.  
  
 Dans les versions antérieures de C\#, les méthodes sont uniquement accessibles en tant que propriétés si la méthode `get` ne comporte aucun paramètre et que la méthode `set` ne contient qu'un seul et unique paramètre de valeur.  Toutefois, toutes les propriétés COM ne sont pas confrontées à ces restrictions.  Par exemple, la propriété [Range](http://go.microsoft.com/fwlink/?LinkId=166053) d'Excel a un accesseur `get` qui requiert un paramètre pour le nom de la plage.  Dans le passé, étant donné que vous n'avez pas pu accéder directement à la propriété `Range`, vous deviez utiliser à la place la méthode `get_Range`, comme indiqué dans l'exemple suivant.  
  
 [!code-cs[csProgGuideIndexedProperties#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_1.cs)]  
  
 Les propriétés indexées vous permettent d'écrire à la place ce qui suit :  
  
 [!code-cs[csProgGuideIndexedProperties#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_2.cs)]  
  
> [!NOTE]
>  L'exemple précédent utilise également la fonctionnalité d'[arguments optionnels](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md), introduite dans Visual C\# 2010, qui vous permet d'omettre `Type.Missing`.  
  
 De la même façon, pour définir la valeur de la propriété `Value` d'un objet [Range](http://go.microsoft.com/fwlink/?LinkId=179211) dans Visual C\# 2008 et versions antérieures, deux arguments sont obligatoires.  L'un fournit un argument pour un paramètre optionnel qui spécifie le type de la valeur de plage.  L'autre fournit la valeur pour la propriété `Value`.  Avant Visual C\# 2010, C\# a autorisé un seul argument.  Par conséquent, au lieu d'utiliser une méthode set normale, vous deviez utiliser la méthode `set_Value` ou une propriété différente, [Value2](http://go.microsoft.com/fwlink/?LinkId=166050).  Les exemples suivants illustrent ces techniques.  Tous deux affectent à la cellule A1 la valeur `Name`.  
  
 [!code-cs[csProgGuideIndexedProperties#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_3.cs)]  
  
 Les propriétés indexées vous permettent d'écrire à la place le code suivant :  
  
 [!code-cs[csProgGuideIndexedProperties#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_4.cs)]  
  
 Vous ne pouvez pas créer vos propres propriétés indexées.  La fonctionnalité prend en charge uniquement l'utilisation des propriétés indexées existantes.  
  
## Exemple  
 Le code suivant illustre un exemple complet.  Pour plus d'informations sur la définition d'un projet qui accède à l'API Office, consultez [Comment : accéder aux objets Office Interop à l'aide des fonctionnalités Visual C\#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).  
  
 [!code-cs[csProgGuideIndexedProperties#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-indexed-properties-in-com-interop-rogramming_5.cs)]  
  
## Voir aussi  
 [Arguments nommés et facultatifs](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)   
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)   
 [Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [Comment : utiliser des arguments nommés et facultatifs dans la programmation Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)   
 [Comment : accéder aux objets Office Interop à l'aide des fonctionnalités Visual C\#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)   
 [Procédure pas à pas : programmation Office](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)