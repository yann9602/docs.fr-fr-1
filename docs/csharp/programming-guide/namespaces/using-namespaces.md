---
title: Utilisation d'espaces de noms (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.names
dev_langs:
- CSharp
helpviewer_keywords:
- fully qualified names [C#]
- namespaces [C#], how to use
ms.assetid: 1fe8bf39-addc-438a-bd9e-86410e32381d
caps.latest.revision: 26
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
ms.openlocfilehash: 61b5d78f1c4924e3858c14876d36e52d4ee46ceb
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-namespaces-c-programming-guide"></a>Utilisation d'espaces de noms (Guide de programmation C#)
Les espaces de noms sont largement utilisés dans les programmes C#, et ce de deux façons différentes. En premier lieu, les classes .NET Framework utilisent les espaces de noms à des fins d’organisation. En deuxième lieu, la déclaration de vos propres espaces de noms peut faciliter le contrôle de la portée des noms de classes et de méthodes dans les projets de programmation de plus grande envergure.  
  
## <a name="accessing-namespaces"></a>Accès aux espaces de noms  
 La plupart des applications C# commencent par une section de directives `using`. Cette section répertorie les espaces de noms que l’application est appelée à utiliser fréquemment et évite au programmeur de spécifier un nom qualifié complet chaque fois qu’une méthode qu’elle contient est utilisée.  
  
 Par exemple, en incluant la ligne :  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_1.cs)]  
  
 Au début d’un programme, le programmeur peut utiliser le code :  
  
 [!code-cs[csProgGuide #31](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_2.cs)]  
  
 À la place de :  
  
 [!code-cs[csProgGuide#30](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/using-namespaces_3.cs)]  
  
## <a name="namespace-aliases"></a>Alias d’espace de noms  
 La [directive using](../../../csharp/language-reference/keywords/using-directive.md) peut aussi servir à créer un alias pour un [espace de noms](../../../csharp/language-reference/keywords/namespace.md). Par exemple, si vous utilisez un espace de noms écrit précédemment qui contient des espaces de noms imbriqués, vous pouvez déclarer un alias pour offrir un moyen rapide d’en référencer un en particulier, comme dans l’exemple suivant :  
  
 [!code-cs[csProgGuideNamespaces#7](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_4.cs)]  
  
## <a name="using-namespaces-to-control-scope"></a>Utilisation d’espaces de noms pour contrôler la portée  
 Le mot clé `namespace` est utilisé pour déclarer une portée. La possibilité de créer des portées au sein de votre projet facilite l’organisation du code et vous permet de créer des types globalement uniques. Dans l’exemple suivant, une classe intitulée `SampleClass` est définie dans deux espaces de noms, l’un étant imbriqué à l’intérieur de l’autre. L’[opérateur .](../../../csharp/language-reference/operators/member-access-operator.md) est utilisé pour différencier la méthode appelée.  
  
 [!code-cs[csProgGuideNamespaces#8](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_5.cs)]  
  
## <a name="fully-qualified-names"></a>Noms qualifiés complets  
 Les espaces de noms et les types portent des titres uniques décrits par des noms qualifiés complets qui indiquent une hiérarchie logique. Par exemple, l’instruction `A.B` implique que `A` est le nom de l’espace de noms ou du type et que `B` est imbriqué en son sein.  
  
 Dans l’exemple suivant, il y a des classes et des espaces de noms imbriqués. Le nom qualifié complet est indiqué sous forme de commentaire à la suite de chaque entité.  
  
 [!code-cs[csProgGuideNamespaces#9](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_6.cs)]  
  
 Dans le segment de code précédent :  
  
-   L’espace de noms `N1` est un membre de l’espace de noms global. Son nom qualifié complet est `N1`.  
  
-   L’espace de noms `N2` est un membre de `N1`. Son nom qualifié complet est `N1.N2`.  
  
-   La classe `C1` est un membre de `N1`. Son nom qualifié complet est `N1.C1`.  
  
-   Le nom de classe `C2` est utilisé deux fois dans ce code. En revanche, les noms qualifiés complets sont uniques. La première instance de `C2` est déclarée à l’intérieur de `C1` ; par conséquent, son nom complet est : `N1.C1.C2`. La deuxième instance de `C2` est déclarée à l’intérieur d’un espace de noms `N2` ; par conséquent, son nom complet est : `N1.N2.C2`.  
  
 À partir du segment de code précédent, vous pouvez ajouter un nouveau membre de classe (`C3`) à l’espace de noms `N1.N2` comme ceci :  
  
 [!code-cs[csProgGuideNamespaces#10](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_7.cs)]  
  
 En règle générale, utilisez `::` pour faire référence à un alias d’espace de noms ou `global::` pour faire référence à l’espace de noms global et `.` pour qualifier les types ou les membres.  
  
 C’est une erreur d’utiliser `::` avec un alias qui fait référence à un type plutôt qu’à un espace de noms. Exemple :  
  
 [!code-cs[csProgGuideNamespaces#11](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_8.cs)]  
  
 [!code-cs[csProgGuideNamespaces#12](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_9.cs)]  
  
 Rappelez-vous que le mot `global` n’est pas un alias prédéfini ; par conséquent, `global.X` n’a pas de signification particulière. Il n’acquiert une signification particulière que lorsqu’il est utilisé avec `::`.  
  
 L’avertissement du compilateur CS0440 est généré si vous définissez un alias nommé global, car `global::` fait toujours référence à l’espace de noms global et non à un alias. Par exemple, la ligne suivante génère l’avertissement :  
  
 [!code-cs[csProgGuideNamespaces#13](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_10.cs)]  
  
 Il est tout à fait opportun d’utiliser `::` avec des alias et cela vous prémunit contre l’introduction inattendue de types supplémentaires. Par exemple, prenons l’exemple suivant :  
  
 [!code-cs[csProgGuideNamespaces#14](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_11.cs)]  
  
 [!code-cs[csProgGuideNamespaces#15](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/using-namespaces_12.cs)]  
  
 Cela fonctionne, mais si un type nommé `Alias` devait par la suite être introduit, `Alias.` se lierait à ce type. L’utilisation de `Alias::Exception` est l’assurance que `Alias` est considéré comme un alias d’espace de noms et qu’il n’est pas pris à tort pour un type.  
  
 Consultez la rubrique [Guide pratique pour utiliser l’alias d’espace de noms global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md) pour plus d’informations sur l’alias `global`.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Espaces de noms](../../../csharp/programming-guide/namespaces/index.md)   
 [Mots clés d’espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [. , opérateur](../../../csharp/language-reference/operators/member-access-operator.md)   
 [::, opérateur](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)   
 [extern](../../../csharp/language-reference/keywords/extern.md)

