---
title: "Comment&#160;: d&#233;finir une &#233;galit&#233; de valeurs pour un type (Guide de programmation&#160;C#) | Microsoft Docs"
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
  - "equals (méthode C#), substituer"
  - "équivalence (C#)"
  - "équivalence d'objets (C#)"
  - "Equals (méthode de substitution C#)"
  - "égalité de valeurs (C#)"
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: d&#233;finir une &#233;galit&#233; de valeurs pour un type (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Lorsque vous définissez une classe ou un struct, vous décidez s'il est utile de créer une définition personnalisée de l'égalité \(ou équivalence\) des valeurs pour le type.  En général, vous implémentez l'égalité des valeurs lorsque les objets du type sont supposés être ajoutés à une collection quelconque ou visent principalement à stocker un ensemble de champs ou de propriétés.  Vous pouvez baser votre définition de l'égalité des valeurs sur une comparaison de tous les champs et propriétés du type, ou bien sur un sous\-ensemble.  Toutefois, dans les deux cas, votre implémentation doit respecter les cinq garanties d'équivalence, à la fois dans les classes et les structs :  
  
1.  x.`Equals`\(x\) retourne `true.` Il s'agit de la propriété réflexive.  
  
2.  x.`Equals`\(y\) retourne la même valeur que y.`Equals`\(x\).  Il s'agit de la propriété symétrique.  
  
3.  Si \(x.`Equals`\(y\) && y.`Equals`\(z\)\) retourne la valeur `true`, x.`Equals`\(z\) retourne la valeur `true`.  Il s'agit de la propriété transitive.  
  
4.  Des appels successifs de x.`Equals`\(y\) retournent la même valeur tant que les objets référencés par x et y ne sont pas modifiés.  
  
5.  x.`Equals`\(null\) retourne la valeur `false`.  Toutefois, la comparaison null.Equals \(null\) lève une exception ; elle ne respecte pas la deuxième règle présentée ci\-dessus.  
  
 Tout struct que vous définissez comporte déjà une implémentation par défaut de l'égalité des valeurs qu'il hérite de la substitution <xref:System.ValueType?displayProperty=fullName> de la méthode <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>.  Cette implémentation utilise la réflexion pour examiner l'ensemble des propriétés et champs publics et non publics du type.  Bien que cette implémentation produise des résultats corrects, elle est relativement lente comparativement à une implémentation personnalisée que vous écrivez spécifiquement pour le type.  
  
 Les détails de l'implémentation de l'égalité des valeurs sont différents pour les classes et les structs.  Toutefois, les classes et les structs requièrent les mêmes étapes de base pour l'implémentation de l'égalité :  
  
1.  Substituez la méthode [virtual](../../../csharp/language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>.  Dans la plupart des cas, votre implémentation de `bool Equals( object obj )` doit uniquement appeler la méthode `Equals` spécifique au type qui correspond à l'implémentation de l'interface <xref:System.IEquatable%601?displayProperty=fullName>.  \(Voir l'étape 2.\)  
  
2.  Implémentez l'interface <xref:System.IEquatable%601?displayProperty=fullName> en fournissant une méthode `Equals` spécifique au type.  C'est à ce stade que la comparaison d'équivalence est réellement effectuée.  Par exemple, vous pouvez décider de définir l'égalité en comparant seulement un ou deux champs de votre type.  Ne levez pas d'exceptions à partir de la méthode `Equals`.  Pour les classes uniquement : cette méthode doit examiner uniquement les champs déclarés dans la classe.  Elle doit appeler `base.Equals` pour examiner des champs qui figurent dans la classe de base.  \(N'effectuez pas cette opération si le type hérite directement de <xref:System.Object> car l'implémentation <xref:System.Object> de <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> effectue une vérification de l'égalité des références.\)  
  
3.  Facultatif, mais recommandé : surchargez les opérateurs [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md) et [\!\=](../../../csharp/language-reference/operators/not-equal-operator.md).  
  
4.  Substituez <xref:System.Object.GetHashCode%2A?displayProperty=fullName> afin que deux objets présentant une égalité des valeurs produisent le même code de hachage.  
  
5.  Facultatif : pour prendre en charge des définitions pour l'opérateur « supérieur à » ou « inférieur à », implémentez l'interface <xref:System.IComparable%601> pour votre type et surchargez également les opérateurs [\<\=](../../../csharp/language-reference/operators/less-than-equal-operator.md) et [\>\=](../../../csharp/language-reference/operators/greater-than-equal-operator.md).  
  
 Le premier exemple suivant présente une implémentation de classe.  Le deuxième exemple présente une implémentation de struct.  
  
## Exemple  
 L'exemple suivant montre comment implémenter l'égalité des valeurs dans une classe \(type référence\).  
  
 [!code-cs[csProgGuideStatements#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_1.cs)]  
  
 Sur les classes \(types référence\), l'implémentation par défaut des deux méthodes <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> effectue une comparaison d'égalité des références, et non pas une vérification de l'égalité des valeurs.  Lorsqu'un implémenteur substitue la méthode virtuelle, l'objectif est de lui donner une sémantique d'égalité des valeurs.  
  
 Les opérateurs `==` et `!=` peuvent être utilisés avec une classe même si celle\-ci ne les surcharge pas.  Toutefois, le comportement par défaut consiste à exécuter une vérification de l'égalité des références.  Dans une classe, si vous surchargez la méthode `Equals`, vous devez également surcharger les opérateurs `==` et `!=` ; toutefois, cette opération n'est pas obligatoire.  
  
## Exemple  
 L'exemple suivant montre comment implémenter l'égalité des valeurs dans un struct \(type valeur\) :  
  
 [!code-cs[csProgGuideStatements#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_2.cs)]  
  
 Pour les structs, l'implémentation par défaut de <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> \(qui est la version substituée dans <xref:System.ValueType?displayProperty=fullName>\) exécute une vérification de l'égalité des valeurs en utilisant la réflexion pour comparer les valeurs de chaque champ du type.  Lorsqu'un implémenteur substitue la méthode `Equals` virtuelle dans un struct, l'objectif est de fournir un moyen plus efficace pour la vérification de l'égalité des valeurs et de baser éventuellement la comparaison sur un sous\-ensemble du champ ou des propriétés du struct.  
  
 Les opérateurs [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md) et [\!\=](../../../csharp/language-reference/operators/not-equal-operator.md) ne peuvent pas s'appliquer à un struct à moins que celui\-ci ne les surcharge explicitement.  
  
## Voir aussi  
 [Comparaisons d'égalité](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)