---
title: "Comment&#160;: concat&#233;ner plusieurs cha&#238;nes (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "concaténer des chaînes (C#)"
  - "joindre des chaînes (C#)"
  - "chaînes (C#), concaténation"
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# Comment&#160;: concat&#233;ner plusieurs cha&#238;nes (Guide de programmation&#160;C#)
La *concaténation* consiste à ajouter une chaîne à la fin d'une autre chaîne.  Lorsque vous concaténez des littéraux de chaîne ou des constantes de chaîne en utilisant l'opérateur `+`, le compilateur crée une chaîne unique.  Aucune concaténation d'exécution ne se produit.  Toutefois, les variables chaîne peuvent être concaténées uniquement au moment de l'exécution.  Dans ce contexte, vous devez comprendre l'impact des diverses approches sur les performances.  
  
## Exemple  
 L'exemple suivant indique comment fractionner un long littéral de chaîne en plus petites chaînes pour améliorer la lisibilité du code source.  Les diverses parties seront concaténées en une chaîne unique lors de la compilation.  Il n'y a aucune incidence sur les performances d'exécution, quel que soit le nombre de chaînes impliquées.  
  
 [!code-cs[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/csharp/CSRefStrings/Strings.cs#30)]  
  
## Exemple  
 Pour concaténer des variables chaîne, vous pouvez utiliser l'opérateur `+` ou `+=` ou la méthode <xref:System.String.Concat%2A?displayProperty=fullName>, <xref:System.String.Format%2A?displayProperty=fullName> ou <xref:System.Text.StringBuilder.Append%2A?displayProperty=fullName>.  L'opérateur `+` est facile à utiliser et convient au code intuitif.  Même si vous utilisez plusieurs opérateurs \+ dans une instruction, le contenu de la chaîne est copié une seule fois.  Mais si vous répétez plusieurs fois cette opération, par exemple dans une boucle, des problèmes de performance peuvent se poser.  Observez par exemple le code suivant :  
  
 [!code-cs[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/csharp/CSRefStrings/Strings.cs#23)]  
  
> [!NOTE]
>  Dans les opérations de concaténation de chaîne, le compilateur C\# traite une chaîne null de la même manière qu'une chaîne vide mais il ne convertit pas la valeur de la chaîne null d'origine.  
  
 Si vous ne concaténez pas un grand nombre de chaînes \(par exemple, dans une boucle\), l'incidence sur les performances de ce code ne sera probablement pas significatif.  Cette remarque s'applique également aux méthodes <xref:System.String.Concat%2A?displayProperty=fullName> et <xref:System.String.Format%2A?displayProperty=fullName>.  
  
 Toutefois, si les performances sont une considération importante, vous devez toujours utiliser la classe <xref:System.Text.StringBuilder> pour concaténer des chaînes.  Le code suivant utilise la méthode <xref:System.Text.StringBuilder.Append%2A> de la classe <xref:System.Text.StringBuilder> pour concaténer des chaînes sans l'effet de chaînage de l'opérateur `+`.  
  
 [!code-cs[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/csharp/CSRefStrings/Strings.cs#22)]  
  
## Voir aussi  
 <xref:System.String>   
 <xref:System.Text.StringBuilder>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)