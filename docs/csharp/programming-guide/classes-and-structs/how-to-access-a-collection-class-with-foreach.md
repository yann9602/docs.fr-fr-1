---
title: "Comment&#160;: acc&#233;der &#224; une classe de collection &#224; l&#39;aide de foreach (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "classes de collection (C#), foreach (instruction)"
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# Comment&#160;: acc&#233;der &#224; une classe de collection &#224; l&#39;aide de foreach (Guide de programmation C#)
L'exemple de code suivant explique comment écrire une classe de collection non générique qui peut être utilisée avec [foreach](../../../csharp/language-reference/keywords/foreach-in.md).  L'exemple définit une classe de générateur de jetons de chaîne.  
  
> [!NOTE]
>  Cet exemple représente uniquement la méthode recommandée dans les cas où vous ne pouvez pas utiliser de classe de collection générique.  Pour obtenir un exemple d'implémentation d'une classe de collection générique de type sécurisé qui prend en charge <xref:System.Collections.Generic.IEnumerable%601>, consultez [Itérateurs](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Dans l'exemple, le segment de code suivant utilise la classe `Tokens` utilise la classe pour décomposer la phrase « ceci est un exemple de phrase. » en jetons à l'aide des séparateurs ' ' et '\-'.  Le code affiche ensuite ces jetons en utilisant une instruction `foreach`.  
  
 [!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## Exemple  
 En interne, la classe `Tokens` utilise un tableau pour stocker les jetons.  Étant donné que les tableaux implémentent <xref:System.Collections.IEnumerator> et <xref:System.Collections.IEnumerable>, l'exemple de code aurait pu utiliser les méthodes d'énumération du tableau \(<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A> et <xref:System.Collections.IEnumerator.Current%2A>\) au lieu de les définir dans la classe `Tokens`.  Les définitions de méthode sont incluses dans l'exemple pour clarifier la façon dont elles sont définies et le rôle de chacune d'entre\-elles.  
  
 [!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 En C\#, il n'est pas nécessaire qu'une classe de collection implémente <xref:System.Collections.IEnumerable> et <xref:System.Collections.IEnumerator> pour être compatible avec `foreach`.  Si la classe possède les membres <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A> et <xref:System.Collections.IEnumerator.Current%2A> requis, cela fonctionnera avec `foreach`.  L'omission des interfaces est intéressante dans la mesure où elle vous permet de définir un type de retour pour `Current` plus spécifique que <xref:System.Object> et d'assurer une sécurité de type.  Cela garantit la sécurité de type.  
  
 Par exemple, modifiez les lignes suivantes dans l'exemple précédent.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Étant donné que `Current` retourne une chaîne, le compilateur peut détecter qu'un type incompatible est utilisé dans une instruction `foreach`, comme indiqué dans le code suivant.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 L'omission de <xref:System.Collections.IEnumerable> et <xref:System.Collections.IEnumerator> présente cependant un inconvénient : la classe de collection ne peut plus fonctionner avec les instructions `foreach`, ou leurs équivalents, des autres langages compatibles avec le CLR \(Common Language Runtime\).  
  
## Voir aussi  
 <xref:System.Collections.Generic>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Collections](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)