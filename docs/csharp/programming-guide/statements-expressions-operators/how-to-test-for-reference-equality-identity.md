---
title: "Comment&#160;: tester l&#39;&#233;galit&#233; des r&#233;f&#233;rences (Identit&#233;) (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "identité d'objet (C#)"
  - "égalité des références (C#)"
ms.assetid: 91307fda-267b-4fd2-a338-2aada39ee791
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# Comment&#160;: tester l&#39;&#233;galit&#233; des r&#233;f&#233;rences (Identit&#233;) (Guide de programmation&#160;C#)
Vous n'avez pas à implémenter de logique personnalisée pour prendre en charge les comparaisons d'égalité des références dans vos types.  Cette fonctionnalité est fournie pour tous les types par la méthode <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> statique.  
  
 L'exemple suivant montre comment déterminer si deux variables présentent une *égalité des références*, ce qui signifie qu'elles font référence au même objet en mémoire.  
  
 L'exemple indique également pourquoi <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> retourne toujours la valeur `false` pour les types valeur et pourquoi vous ne devriez pas utiliser  <xref:System.Object.ReferenceEquals%2A> pour déterminer l'égalité de chaînes.  
  
## Exemple  
 [!code-cs[csProgGuideObjects#90](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-test-for-referenc_1.cs)]  
  
 L'implémentation de `Equals` dans la classe de base universelle <xref:System.Object?displayProperty=fullName> exécute également une vérification de l'égalité des références, mais il est recommandé de ne pas l'utiliser car, si une classe se substitue à la méthode, vous risquez de ne pas obtenir les résultats attendus.  Cette remarque s'applique également aux opérateurs `==` et `!=`.  Lorsqu'ils s'appliquent aux types référence, le comportement par défaut de \=\= et `!=` consiste à effectuer une vérification de l'égalité des références.  Toutefois, les classes dérivées peuvent surcharger l'opérateur pour effectuer une vérification de l'égalité des valeurs.  Pour réduire le risque d'erreurs, il est recommandé d'utiliser systématiquement <xref:System.Object.ReferenceEquals%2A> lorsque vous devez déterminer si deux objets présentent une égalité des références.  
  
 Les chaînes constantes d'un même assembly sont toujours internées par le runtime.  Autrement dit, une seule instance de chaque chaîne littérale unique est conservée.  Toutefois, le runtime ne garantit pas que les chaînes créées au moment de l'exécution sont internées, ni que deux chaînes constantes égales d'assemblys différents sont internées.  
  
## Voir aussi  
 [Comparaisons d'égalité](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)