---
title: "Domaine d&#39;accessibilit&#233; (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "domaine d'accessibilité (C#)"
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# Domaine d&#39;accessibilit&#233; (r&#233;f&#233;rence C#)
Le domaine d'accessibilité d'un membre indique dans quelles sections du programme un membre peut être référencé.  Si le membre est imbriqué dans un autre type, son domaine d'accessibilité est déterminé à la fois par le [niveau d'accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) du membre et par le domaine d'accessibilité du type conteneur immédiat.  
  
 Le domaine d'accessibilité d'un type de niveau supérieur correspond au moins à la programmation du projet dans lequel il est déclaré.  Autrement dit, le domaine inclut tous les fichiers sources de ce projet.  Le domaine d'accessibilité d'un type imbriqué correspond au moins au texte du programme du type dans lequel il est déclaré.  Autrement dit, le domaine est le corps du type, ce qui inclut tous les types imbriqués.  Le domaine d'accessibilité d'un type imbriqué ne dépasse jamais celui du type conteneur.  Ces concepts sont illustrés dans l'exemple ci\-dessous.  
  
## Exemple  
 Cet exemple met en jeu un type de niveau supérieur, `T1`, et deux classes imbriquées, `M1` et `M2`.  Les classes contiennent des champs dotés d'accessibilités déclarées différentes.  Dans la méthode `Main`, un commentaire suit chaque instruction pour indiquer le domaine d'accessibilité de chaque membre.  Notez que les instructions qui tentent de référencer les membres inaccessibles ont été placées en commentaire.  Si vous voulez examiner les erreurs de compilation causées par la référence à un membre inaccessible, supprimez une marque de commentaire à chaque fois.  
  
 [!code-cs[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs d'accès](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Niveaux d'accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Limitations sur l'utilisation des niveaux d'accessibilité](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)   
 [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [privées](../../../csharp/language-reference/keywords/private.md)   
 [protégés](../../../csharp/language-reference/keywords/protected.md)   
 [interne](../../../csharp/language-reference/keywords/internal.md)