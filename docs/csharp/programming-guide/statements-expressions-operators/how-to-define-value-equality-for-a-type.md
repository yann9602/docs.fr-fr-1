---
title: "Guide pratique pour définir une égalité de valeurs pour un type (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#] , overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e008be022765ff7d2bb440f0a37193b882038b76
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Guide pratique pour définir une égalité de valeurs pour un type (Guide de programmation C#)
Quand vous définissez une classe ou un struct, vous décidez s’il est judicieux de créer une définition personnalisée de l’égalité des valeurs (ou équivalence) pour le type. En général, vous implémentez l’égalité des valeurs quand des objets du type sont supposés être ajoutés à une collection quelconque, ou quand leur objectif principal est de stocker un ensemble de champs ou propriétés. Vous pouvez baser votre définition de l’égalité des valeurs sur une comparaison de tous les champs et propriétés du type, ou vous pouvez la baser sur un sous-ensemble. Dans les deux cas, et dans les classes et les structs, votre implémentation doit respecter les cinq garanties d’équivalence :  
  
1.  x.`Equals`(x) retourne `true.` Il s’agit de la propriété réflexive.  
  
2.  x.`Equals`(y) retourne la même valeur que y.`Equals`(x). Il s’agit de la propriété symétrique.  
  
3.  Si (x.`Equals`(y) && y.`Equals`(z)) retourne `true`, x.`Equals`(z) retourne `true`. Il s’agit de la propriété transitive.  
  
4.  Les appels successifs de x.`Equals`(y) retournent la même valeur tant que les objets référencés par x et y ne sont pas modifiés.  
  
5.  x.`Equals`(null) retourne `false`. Toutefois, null.Equals(null) lève une exception. Elle ne respecte pas la règle n°2 ci-dessus.  
  
 Tout struct que vous définissez a déjà une implémentation par défaut de l’égalité des valeurs dont il hérite de la substitution <xref:System.ValueType?displayProperty=fullName> de la méthode <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>. Cette implémentation utilise la réflexion pour examiner tous les champs et propriétés du type. Bien que cette implémentation produise des résultats corrects, elle est relativement lente par rapport à une implémentation personnalisée que vous écrivez spécifiquement pour le type.  
  
 Les détails d’implémentation pour l’égalité des valeurs sont différents pour les classes et les structs. Toutefois, les classes et les structs nécessitent tous deux les mêmes étapes de base pour l’implémentation de l’égalité :  
  
1.  Substituez la méthode [virtual](../../../csharp/language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>. Dans la plupart des cas, votre implémentation de `bool Equals( object obj )` doit simplement appeler la méthode `Equals` propre au type qui est l’implémentation de l’interface <xref:System.IEquatable%601?displayProperty=fullName>. (Voir l’étape 2.)  
  
2.  Implémentez l’interface <xref:System.IEquatable%601?displayProperty=fullName> en fournissant une méthode `Equals` propre au type. C’est ici qu’est effectuée la comparaison d’équivalence. Par exemple, vous pouvez décider de définir l’égalité en comparant seulement un ou deux champs de votre type. Ne levez pas d'exceptions à partir de la méthode `Equals`. Pour les classes uniquement : cette méthode doit examiner uniquement les champs qui sont déclarés dans la classe. Elle doit appeler `base.Equals` pour examiner les champs qui sont dans la classe de base. (Ne faites pas cela si le type hérite directement d’<xref:System.Object>, car l’implémentation <xref:System.Object> de <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> effectue une vérification de l’égalité de référence.)  
  
3.  Facultatif, mais recommandé : Surchargez les opérateurs [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) et [! =](../../../csharp/language-reference/operators/not-equal-operator.md).  
  
4.  Substituez <xref:System.Object.GetHashCode%2A?displayProperty=fullName> pour que deux objets ayant une égalité des valeurs produisent le même code de hachage.  
  
5.  Facultatif : Pour prendre en charge les définitions pour « supérieur à » ou « inférieur à », implémentez l’interface <xref:System.IComparable%601> pour votre type, et surchargez également les opérateurs [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) et [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md).  
  
 Le premier exemple qui suit illustre une implémentation de classe. Le deuxième exemple illustre une implémentation de struct.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter l’égalité des valeurs dans une classe (type référence).  
  
 [!code-cs[csProgGuideStatements#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_1.cs)]  
  
 Sur les classes (types référence), l’implémentation par défaut des deux méthodes <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> effectue une comparaison d’égalité de référence, et non une vérification de l’égalité des valeurs. Quand un implémenteur substitue la méthode virtuelle, l’objectif est de lui donner une sémantique d’égalité des valeurs.  
  
 Les opérateurs `==` et `!=` peuvent être utilisés avec des classes, même si la classe ne les surcharge pas. Toutefois, le comportement par défaut consiste à effectuer une vérification de l’égalité de référence. Dans une classe, si vous surchargez la méthode `Equals`, vous devez surcharger les opérateurs `==` et `!=`, mais cela n’est pas obligatoire.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment implémenter l’égalité des valeurs dans un struct (type valeur) :  
  
 [!code-cs[csProgGuideStatements#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_2.cs)]  
  
 Pour les structs, l’implémentation par défaut de <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> (qui est la version substituée dans <xref:System.ValueType?displayProperty=fullName>) effectue une vérification de l’égalité des valeurs à l’aide de la réflexion pour comparer les valeurs de chaque champ dans le type. Quand un implémenteur substitue la méthode `Equals` virtuelle dans un struct, l’objectif est de fournir un moyen plus efficace d’effectuer la vérification de l’égalité des valeurs, et éventuellement de baser la comparaison sur un sous-ensemble des propriétés ou du champ du struct.  
  
 Les opérateurs [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) et [!=](../../../csharp/language-reference/operators/not-equal-operator.md) ne peuvent pas opérer sur un struct, sauf si le struct les surcharge explicitement.  
  
## <a name="see-also"></a>Voir aussi  
 [Comparaisons d’égalité](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)

