---
title: "Comment : concaténer plusieurs chaînes (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca240523e2483289e11433fd58d9630a31721b33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a>Comment : concaténer plusieurs chaînes (Guide de programmation C#)
La *concaténation* consiste à ajouter une chaîne à la fin d’une autre chaîne. Quand vous concaténez des littéraux de chaîne ou des constantes de chaîne en utilisant l’opérateur `+`, le compilateur crée une chaîne unique. Aucune concaténation d’exécution ne se produit. Toutefois, les variables chaîne peuvent être concaténées uniquement au moment de l’exécution. Dans ce contexte, vous devez comprendre l’impact des diverses approches sur les performances.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant indique comment fractionner un long littéral de chaîne en plus petites chaînes pour améliorer la lisibilité du code source. Les diverses parties seront concaténées en une chaîne unique lors de la compilation. Il n’y a aucune incidence sur les performances d’exécution, quel que soit le nombre de chaînes impliquées.  
  
 [!code-csharp[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## <a name="example"></a>Exemple  
 Pour concaténer des variables chaîne, vous pouvez utiliser l’opérateur `+` ou `+=`, ou la méthode <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>. L’opérateur `+` est facile à utiliser et convient au code intuitif. Même si vous utilisez plusieurs opérateurs + dans une instruction, le contenu de la chaîne est copié une seule fois. Toutefois, si vous répétez plusieurs fois cette opération, par exemple dans une boucle, des problèmes d’efficacité peuvent se poser. Observez par exemple le code suivant :  
  
 [!code-csharp[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  Dans les opérations de concaténation de chaîne, le compilateur C# traite une chaîne null de la même manière qu’une chaîne vide, mais il ne convertit pas la valeur de la chaîne null d’origine.  
  
 Si vous ne concaténez pas un grand nombre de chaînes (par exemple, dans une boucle), l’incidence de ce code sur les performances ne sera probablement pas significative. Cette remarque s’applique également aux méthodes <xref:System.String.Concat%2A?displayProperty=nameWithType> et <xref:System.String.Format%2A?displayProperty=nameWithType>.  
  
 Toutefois, si les performances sont une considération importante, vous devez toujours utiliser la classe <xref:System.Text.StringBuilder> pour concaténer des chaînes. Le code suivant utilise la méthode <xref:System.Text.StringBuilder.Append%2A> de la classe <xref:System.Text.StringBuilder> pour concaténer des chaînes sans l’effet de chaînage de l’opérateur `+`.  
  
 [!code-csharp[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Chaînes](../../../csharp/programming-guide/strings/index.md)
