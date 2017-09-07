---
title: "Méthodes anonymes (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: 31
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
ms.openlocfilehash: 92842becf26a15ab1a6f5e9621002abf71dc67bc
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="anonymous-methods-c-programming-guide"></a>Méthodes anonymes (Guide de programmation C#)
Dans les versions de C# antérieures à 2.0, la seule façon de déclarer un type [delegate](../../../csharp/language-reference/keywords/delegate.md) consistait à utiliser des [méthodes nommées](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md). C# 2.0 a introduit les méthodes anonymes et dans C# 3.0 et ultérieur, les expressions lambda remplacent les méthodes anonymes comme meilleur moyen d’écrire du code « in line ». Toutefois, les informations relatives aux méthodes anonymes figurant dans cette rubrique s’appliquent également aux expressions lambda. Il existe un cas où une méthode anonyme fournit des fonctionnalités non disponibles dans les expressions lambda. Les méthodes anonymes vous permettent d’omettre la liste de paramètres. Cela signifie qu’une méthode anonyme peut être convertie en délégués avec diverses signatures. Cela n’est pas possible avec les expressions lambda. Pour plus d’informations spécifiques aux expressions lambda, consultez [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 La création de méthodes anonymes est essentiellement un moyen de passer un bloc de code comme paramètre de délégué. Voici deux exemples :  
  
 [!code-cs[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-cs[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 En utilisant des méthodes anonymes, vous réduisez la surcharge liée au codage dans l’instanciation de délégués, car vous n’avez pas à créer de méthode distincte.  
  
 Par exemple, la spécification d’un bloc de code au lieu d’un délégué peut être utile dans une situation où la surcharge que représente la création d’une méthode ne semble pas justifiée. Un bon exemple pourrait être le moment où vous démarrez un nouveau thread. Cette classe crée un thread et contient également le code exécuté par le thread sans créer une méthode supplémentaire pour le délégué.  
  
 [!code-cs[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a>Remarques  
 La portée des paramètres d’une méthode anonyme est *bloc-méthode-anonyme*.  
  
 C’est une erreur d’avoir une instruction de saut, telle que [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md) ou [continue](../../../csharp/language-reference/keywords/continue.md), à l’intérieur du bloc de méthode anonyme si la cible est à l’extérieur du bloc. C’est également une erreur d’avoir une instruction de saut, telle que `goto`, `break` ou `continue`, à l’extérieur du bloc de méthode anonyme si la cible est à l’intérieur du bloc.  
  
 Les variables locales et les paramètres dont la portée contient une déclaration de méthode anonyme sont appelés variables *externes* de la méthode anonyme. Par exemple, dans le segment de code suivant, `n` est une variable externe :  
  
 [!code-cs[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 Une référence à la variable externe `n` est dite *capturée* quand le délégué est créé. Contrairement aux variables locales, la durée de vie d’une variable capturée s’étend jusqu’à ce que les délégués qui font référence aux méthodes anonymes soient éligibles pour le garbage collection.  
  
 Une méthode anonyme ne peut pas accéder aux paramètres [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md) d’une portée externe.  
  
 Aucun code unsafe n’est accessible dans le *bloc-méthode-anonyme*.  
  
 Les méthodes anonymes ne sont pas autorisées à gauche de l’opérateur [is](../../../csharp/language-reference/keywords/is.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant présente deux façons d’instancier un délégué :  
  
-   Association du délégué à une méthode anonyme.  
  
-   Association du délégué à une méthode nommée (`DoWork`).  
  
 Dans chaque cas, un message s’affiche quand le délégué est appelé.  
  
 [!code-cs[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)   
 [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Délégués avec méthodes nommées et méthodes anonymes](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)

