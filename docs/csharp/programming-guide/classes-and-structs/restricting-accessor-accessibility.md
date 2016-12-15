---
title: "Restriction d&#39;accessibilit&#233; de l&#39;accesseur (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "accesseurs (C#)"
  - "accessibilité de l'accesseur asymétrique (C#)"
  - "indexeurs (C#), en lecture seule"
  - "propriétés (C#), en lecture seule"
  - "lecture seule (indexeurs C#)"
  - "lecture seule (propriétés C#)"
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Restriction d&#39;accessibilit&#233; de l&#39;accesseur (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les parties [get](../../../csharp/language-reference/keywords/get.md) et [set](../../../csharp/language-reference/keywords/set.md) d'une propriété ou d'un indexeur s'appellent des *accesseurs*.  Par défaut, ces accesseurs ont la même visibilité, ou niveau d'accès : celle de la propriété ou de l'indexeur auquel ils appartiennent.  Pour plus d'informations, consultez [niveaux d'accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md).  Toutefois, il peut s'avérer utile de restreindre l'accès à l'un de ces accesseurs.  En général, cela implique de restreindre l'accessibilité de l'accesseur `set`, tout en gardant l'accesseur `get` publiquement accessible.  Par exemple :  
  
 [!code-cs[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]  
  
 Dans cet exemple, une propriété appelée `Name` définit un accesseur `get` et `set`.  L'accesseur `get` reçoit le niveau d'accessibilité de la propriété elle\-même, `public` dans ce cas, alors que l'accesseur `set` est restreint explicitement par l'application du modificateur d'accès [protected](../../../csharp/language-reference/keywords/protected.md) à l'accesseur lui\-même.  
  
## Restrictions sur les modificateurs d'accès sur les accesseurs  
 L'utilisation des modificateurs d'accesseurs sur les propriétés ou les indexeurs est soumise aux conditions suivantes :  
  
-   Vous ne pouvez pas utiliser de modificateurs d'accesseur sur une interface ou une implémentation de membre d'[interface](../../../csharp/language-reference/keywords/interface.md) explicite.  
  
-   Vous pouvez utiliser les modificateurs d'accesseur uniquement si la propriété ou l'indexeur dispose à la fois d'accesseurs `set` et `get`.  Dans ce cas, le modificateur est autorisé sur uniquement un des deux accesseurs.  
  
-   Si la propriété ou l'indexeur possède un modificateur [override](../../../csharp/language-reference/keywords/override.md), le modificateur d'accesseur doit correspondre à l'accesseur de l'accesseur substitué, le cas échant.  
  
-   Le niveau d'accessibilité sur l'accesseur doit être plus restrictif que le niveau d'accessibilité sur la propriété ou l'indexeur même.  
  
## Modificateurs d'accès sur les accesseurs de substitution  
 Lorsque vous substituez une propriété ou un indexeur, les accesseurs remplacés doivent être accessibles au code de substitution.  Par ailleurs, le niveau d'accessibilité à la fois de la propriété et de l'indexeur, ainsi que celui des accesseurs doit correspondre à la propriété\/l'indexeur et aux accesseurs substitués correspondants.  Par exemple :  
  
 [!code-cs[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]  
  
## Implémentation d'interfaces  
 Lorsque vous utilisez un accesseur pour implémenter une interface, l'accesseur peut ne pas avoir de modificateur d'accès.  Toutefois, si vous implémentez l'interface à l'aide d'un accesseur, tel que `get`, l'autre accesseur peut avoir un modificateur d'accès, comme dans l'exemple suivant :  
  
 [!code-cs[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]  
  
## Domaine d'accessibilité de l'accesseur  
 Si vous utilisez un modificateur d'accès sur l'accesseur, le [domaine d'accessibilité](../../../csharp/language-reference/keywords/accessibility-domain.md) de l'accesseur est déterminé par ce modificateur.  
  
 Si vous n'avez pas utilisé un modificateur d'accès sur l'accesseur, le domaine d'accessibilité de l'accesseur est déterminé par le niveau d'accessibilité de la propriété ou de l'indexeur.  
  
## Exemple  
 L'exemple suivant contient trois classes, `BaseClass`, `DerivedClass` et `MainClass`.  Il y a deux propriétés sur `BaseClass`, `Name` et `Id` sur les deux classes.  L'exemple montre comment la propriété `Id` sur `DerivedClass` peut être masquée par la propriété `Id` sur `BaseClass` lorsque vous utilisez un modificateur d'accès restrictif tel que [protected](../../../csharp/language-reference/keywords/protected.md) ou [private](../../../csharp/language-reference/keywords/private.md).  Par conséquent, lorsque vous assignez des valeurs à cette propriété, la propriété sur la classe `BaseClass` est appelée à la place.  Le remplacement du modificateur d'accès par [public](../../../csharp/language-reference/keywords/public.md) rend la propriété accessible.  
  
 L'exemple montre également qu'un modificateur d'accès restrictif, tel que `private` ou `protected`, sur l'accesseur `set` de la propriété `Name` dans `DerivedClass` empêche l'accès à l'accesseur et génère une erreur lorsque vous le lui assignez.  
  
 [!code-cs[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]  
  
## Commentaires  
 Notez que si vous remplacez la déclaration `new private string Id` par `new public string Id`, vous obtenez la sortie :  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Indexeurs](../../../csharp/programming-guide/indexers/index.md)   
 [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)