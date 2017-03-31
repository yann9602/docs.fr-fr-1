---
title: "Gestion de version avec les mots clés override et new (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
caps.latest.revision: 25
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b464b4c395af093bb9124bb671c5c212c750f497
ms.lasthandoff: 03/13/2017

---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Versioning avec les mots clés override et new (Guide de programmation C#)
Le langage C# est conçu de telle sorte que la gestion de version entre les classes de [base](../../../csharp/language-reference/keywords/base.md) et les classes dérivées dans différentes bibliothèques puisse évoluer et préserver une compatibilité descendante. Cela signifie, par exemple, que l’introduction dans une [classe](../../../csharp/language-reference/keywords/class.md) de base d’un nouveau membre portant le même nom qu’un membre dans une classe dérivée est totalement prise en charge par C# et n’engendre pas de comportement imprévisible. Cela signifie également qu'une classe doit indiquer de façon explicite si une méthode est conçue pour se substituer à une méthode héritée ou s'il s'agit d'une nouvelle méthode qui masque une méthode héritée portant un nom similaire.  
  
 Dans C#, les classes dérivées peuvent contenir des méthodes portant le même nom que des méthodes de classe de base.  
  
-   La méthode de classe de base doit être définie comme [virtuelle](../../../csharp/language-reference/keywords/virtual.md).  
  
-   Si la méthode dans la classe dérivée n’est pas précédée des mots clés [new](../../../csharp/language-reference/keywords/new.md) ou [override](../../../csharp/language-reference/keywords/override.md), le compilateur émet un avertissement et la méthode se comporte comme si le mot clé `new` était présent.  
  
-   Si la méthode dans la classe dérivée est précédée du mot clé `new`, la méthode est définie comme étant indépendante de la méthode dans la classe de base.  
  
-   Si la méthode dans la classe dérivée est précédée du mot clé `override`, les objets de la classe dérivée appelleront cette méthode plutôt que la méthode de la classe de base.  
  
-   La méthode de la classe de base peut être appelée à partir de la classe dérivée à l’aide du mot clé `base`.  
  
-   Les mots clés `override`, `virtual` et `new` peuvent également être appliqués aux propriétés, indexeurs et événements.  
  
 Par défaut, les méthodes C# ne sont pas virtuelles. Si une méthode est déclarée comme virtuelle, toute classe héritant de la méthode peut implémenter sa propre version. Pour créer une méthode virtuelle, le modificateur `virtual` est utilisé dans la déclaration de méthode de la classe de base. La classe dérivée peut ensuite remplacer la méthode virtuelle de base avec le mot clé `override` ou masquer la méthode virtuelle dans la classe de base avec le mot clé `new`. Si ni le mot clé `override` ni le mot clé `new` ne sont spécifiés, le compilateur émettra un avertissement et la méthode dans la classe dérivée masquera la méthode dans la classe de base.  
  
 Pour illustrer ceci dans un exemple pratique, supposons un instant que la Société A ait créé une classe nommée `GraphicsClass` que votre programme utilise. Les éléments suivants représentent `GraphicsClass` :  
  
 [!code-cs[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]  
  
 Votre société utilise cette classe, et vous l’utilisez pour dériver votre propre classe, en ajoutant une nouvelle méthode :  
  
 [!code-cs[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]  
  
 Votre application est utilisée sans problèmes, jusqu’à ce que la Société A publie une nouvelle version de `GraphicsClass`, qui ressemble au code suivant :  
  
 [!code-cs[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]  
  
 La nouvelle version de `GraphicsClass` contient maintenant une méthode nommée `DrawRectangle`. Initialement, rien ne se produit. La nouvelle version est encore compatible au format binaire avec l’ancienne version. Tous les logiciels que vous avez déployés continueront de fonctionner, même si la nouvelle classe est installée sur ces systèmes informatiques. Tout appel existant à la méthode `DrawRectangle` continuera de faire référence à votre version, dans votre classe dérivée.  
  
 Toutefois, dès que vous recompilerez votre application à l’aide de la nouvelle version de `GraphicsClass`, vous recevrez un avertissement du compilateur, CS0108. Cet avertissement vous informe que vous devez envisager la façon dont vous souhaitez que votre méthode `DrawRectangle` se comporte dans votre application.  
  
 Si vous souhaitez que votre méthode remplace la nouvelle méthode de la classe de base, utilisez le mot clé `override` :  
  
 [!code-cs[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]  
  
 Le mot clé `override` garantit que tous les objets dérivés de `YourDerivedGraphicsClass` utiliseront la version de classe dérivée de `DrawRectangle`. Les objets dérivés de `YourDerivedGraphicsClass` peuvent toujours accéder à la version de la classe de base de `DrawRectangle` à l’aide du mot clé base :  
  
 [!code-cs[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]  
  
 Si vous ne souhaitez pas que votre méthode se substitue à la nouvelle méthode de la classe de base, prenez en compte les considérations suivantes. Pour éviter toute confusion entre les deux méthodes, vous pouvez renommer votre méthode. Ceci peut prendre du temps et constituer un risque d’erreur ou bien ne pas être tout simplement pratique dans certains cas. Toutefois, si votre projet est relativement petit, vous pouvez utiliser les options de refactorisation de Visual Studio pour renommer la méthode. Pour plus d’informations, consultez [Refactorisation des classes et des types (Concepteur de classes)](https://docs.microsoft.com/visualstudio/ide/refactoring-classes-and-types-class-designer).  
  
 Sinon, vous pouvez éviter de recevoir l’avertissement à l’aide du mot clé `new` dans la définition de votre classe dérivée :  
  
 [!code-cs[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]  
  
 L’utilisation du mot clé `new` indique au compilateur que votre définition masque la définition qui est contenue dans la classe de base. Il s'agit du comportement par défaut.  
  
## <a name="override-and-method-selection"></a>Substitution et sélection de méthode  
 Lorsqu'une méthode est appelée sur une classe, le compilateur C# sélectionne la meilleure méthode à appeler si plusieurs méthodes sont compatibles avec l'appel, comme lorsque deux méthodes portent les mêmes noms et dont les paramètres sont compatibles avec les paramètres transmis. Les méthodes suivantes seraient compatibles :  
  
 [!code-cs[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]  
  
 Quand `DoWork` est appelée sur une instance de `Derived`, le compilateur C# essaie d’abord de rendre l’appel compatible avec les versions de `DoWork` déclarées à l’origine sur `Derived`. Les méthodes override ne sont pas considérées comme déclarées sur une classe ; il s’agit de nouvelles implémentations d’une méthode déclarée sur une classe de base. Le compilateur C# essaiera de faire correspondre l’appel à une méthode substituée portant le même nom et avec des paramètres compatibles uniquement s’il ne parvient pas à faire correspondre l’appel de méthode à une méthode d’origine sur `Derived`. Exemple :  
  
 [!code-cs[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]  
  
 Étant donné que la variable `val` peut être convertie implicitement en un double, le compilateur C# appelle `DoWork(double)` au lieu de `DoWork(int)`. Il existe deux façons d’éviter ceci. Premièrement, évitez de déclarer de nouvelles méthodes portant le même nom que des méthodes virtuelles. Deuxièmement, vous pouvez indiquer au compilateur C# d’appeler la méthode virtuelle en le faisant chercher dans la liste de méthodes de la classe de base par casting de l’instance `Derived` en `Base`. Étant donné que la méthode est virtuelle, l’implémentation de `DoWork(int)` sur `Derived` sera appelée. Exemple :  
  
 [!code-cs[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]  
  
 Pour obtenir d’autres exemples des mots clés `new` et `override`, consultez [Savoir quand utiliser les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
