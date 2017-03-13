---
title: "Mot cl&#233; default dans le code g&#233;n&#233;rique (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "default (mot clé C#), programmation générique"
  - "génériques (C#), default (mot clé)"
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# Mot cl&#233; default dans le code g&#233;n&#233;rique (Guide de programmation C#)
Dans les classes et méthodes génériques se pose le problème de savoir comment assigner une valeur par défaut à un type paramétré T lorsque vous ne savez pas ce qui suit à l'avance :  
  
-   Si T sera un type référence ou un type valeur.  
  
-   Si T est un type valeur, s'il sera une valeur numérique ou un struct.  
  
 Étant donnée une variable t d'un type paramétré T, l'instruction t \= null est valide uniquement si T est un type référence et t \= 0 fonctionneront seulement pour les types valeur numériques mais pas pour les struct.  La solution est d'utiliser le mot clé `default`, qui retournera la valeur Null pour les types référence et zéro pour les types valeur numériques.  Pour les struct, il retournera chaque membre du struct initialisé à zéro ou null, selon qu'il s'agit de types valeur ou référence.  Pour les types valeur Nullable, la valeur par défaut retourne <xref:System.Nullable%601?displayProperty=fullName>, initialisé comme tout struct.  
  
 L'exemple suivant de la classe `GenericList<T>` montre comment utiliser le mot clé `default`.  Pour plus d'informations, consultez [Vue d'ensemble des génériques](../../../csharp/programming-guide/generics/introduction-to-generics.md).  
  
 [!code-cs[csProgGuideGenerics#41](../../../csharp/programming-guide/generics/codesnippet/CSharp/default-keyword-in-generic-code_1.cs)]  
  
## Voir aussi  
 <xref:System.Collections.Generic>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Génériques](../../../csharp/programming-guide/generics/index.md)   
 [Méthodes génériques](../../../csharp/programming-guide/generics/generic-methods.md)   
 [Génériques](../Topic/Generics%20in%20the%20.NET%20Framework.md)