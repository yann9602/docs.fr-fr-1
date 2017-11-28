---
title: "Utilisation de délégués (guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: delegates [C#], how to use
ms.assetid: 99a2fc27-a32e-4a34-921c-e65497520eec
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cef62448388299f310fa26ecb632485b6538c032
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-delegates-c-programming-guide"></a>Utilisation de délégués (guide de programmation C#)
Un [délégué](../../../csharp/language-reference/keywords/delegate.md) est un type qui encapsule sans risque une méthode ; il est similaire à un pointeur de fonction en C et C++. Toutefois, à la différence des pointeurs de fonction C, les délégués sont orientés objet, de type sécurisé et sûrs. Le type d'un délégué est défini par le nom du délégué. L’exemple suivant déclare un délégué nommé `Del` qui peut encapsuler une méthode acceptant une chaîne ([string](../../../csharp/language-reference/keywords/string.md)) comme argument et qui retourne [void](../../../csharp/language-reference/keywords/void.md) :  
  
 [!code-csharp[csProgGuideDelegates#21](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_1.cs)]  
  
 Un objet de délégué est normalement construit en fournissant le nom de la méthode que le délégué encapsule, ou avec une [méthode anonyme](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md). Une fois qu'un délégué est instancié, un appel de méthode fait au délégué est transmis par le délégué à cette méthode. Les paramètres passés au délégué par l'appelant sont passés à la méthode et la valeur de retour de la méthode, le cas échéant, est retournée à l'appelant par le délégué. Cette opération est connue sous le nom d'appel du délégué. Un délégué instancié peut être appelé comme s'il s'agissait de la méthode encapsulée elle-même. Par exemple :  
  
 [!code-csharp[csProgGuideDelegates#22](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_2.cs)]  
  
 [!code-csharp[csProgGuideDelegates#23](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_3.cs)]  
  
 Les types délégués sont dérivés de la classe <xref:System.Delegate> du .NET Framework. Les types délégués sont scellés ([sealed<xref:System.Delegate>), c’est-à-dire qu’ils ne peuvent pas être faire l’objet d’une dérivation, et il n’est pas possible de dériver des classes personnalisées à partir de ](../../../csharp/language-reference/keywords/sealed.md). Étant donné que le délégué instancié est un objet, il peut être passé comme paramètre ou assigné à une propriété. Cela permet à une méthode d'accepter un délégué comme paramètre et d'appeler le délégué ultérieurement. Cette opération est connue sous le nom de rappel asynchrone et constitue une méthode courante pour notifier un appelant quand un long processus s'est achevé. Lorsqu'un délégué est ainsi utilisé, le code qui utilise le délégué n'a pas besoin de connaître l'implémentation de la méthode utilisée. La fonctionnalité est semblable à l'encapsulation que fournissent les interfaces.  
  
 Une autre utilisation courante des rappels consiste à définir une méthode de comparaison personnalisée et à passer ce délégué à une méthode de tri. Le code de l'appelant peut ainsi faire partie de l'algorithme de tri. L'exemple de méthode suivant utilise le type `Del` comme paramètre :  
  
 [!code-csharp[csProgGuideDelegates#24](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_4.cs)]  
  
 Vous pouvez ensuite passer le délégué créé ci-dessus à cette méthode :  
  
 [!code-csharp[csProgGuideDelegates#25](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_5.cs)]  
  
 et vous recevez le résultat suivant sur la console :  
  
 `The number is: 3`  
  
 En utilisant le délégué comme abstraction, `MethodWithCallback` n'a pas besoin d'appeler la console directement. La méthode n'a pas à être conçue en l'associant obligatoirement à une console. En effet, `MethodWithCallback` se contente de préparer une chaîne et de la passer à une autre méthode. Cela est particulièrement efficace, car une méthode déléguée peut utiliser n'importe quel nombre de paramètres.  
  
 Quand un délégué est construit pour encapsuler une méthode d'instance, le délégué fait référence à l'instance et à la méthode. Un délégué n'ayant aucune connaissance du type d'instance hormis la méthode qu'il encapsule, un délégué peut faire référence à n'importe quel type d'objet tant qu'il existe une méthode sur l'objet correspondant à la signature du délégué. Quand un délégué est construit pour encapsuler une méthode statique, il fait uniquement référence à la méthode. Prenons les déclarations suivantes :  
  
 [!code-csharp[csProgGuideDelegates#26](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_6.cs)]  
  
 Avec la méthode statique `DelegateMethod` montrée précédemment, nous avons désormais trois méthodes pouvant être encapsulées par une instance `Del`.  
  
 Un délégué peut appeler plusieurs méthodes quand il est appelé. Cette opération se nomme multidiffusion. L'ajout d'une méthode supplémentaire à la liste des méthodes du délégué – la liste d'invocation – nécessite simplement l'ajout de deux délégués à l'aide des opérateurs d'addition ou d'assignation d'addition (« + » ou « += »). Par exemple :  
  
 [!code-csharp[csProgGuideDelegates#27](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_7.cs)]  
  
 À ce stade, `allMethodsDelegate` contient trois méthodes dans sa liste d'invocation : `Method1`, `Method2` et `DelegateMethod`. Les trois délégués initiaux, `d1`, `d2` et `d3`, restent inchangés. Lors de l'appel de `allMethodsDelegate`, les trois méthodes sont appelées dans l'ordre. Si le délégué utilise des paramètres de référence, la référence est passée séquentiellement à chacune des trois méthodes et toute modification apportée par une méthode est visible dans la méthode suivante. Quand l'une des méthodes lève une exception qui n'est pas interceptée dans la méthode, cette exception est passée à l'appelant du délégué et aucune des méthodes suivantes dans la liste d'invocation n'est appelée. Si le délégué a une valeur de retour et/ou des paramètres out, il retourne la valeur de retour et les paramètres de la dernière méthode appelée. Pour supprimer une méthode de la liste d'invocation, utilisez l'opérateur de décrémentation ou d'assignation de décrémentation (« - » ou « -= »). Par exemple :  
  
 [!code-csharp[csProgGuideDelegates#28](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_8.cs)]  
  
 Étant donné que les types délégués sont dérivés de `System.Delegate`, les méthodes et les propriétés définies par cette classe peuvent être appelées sur le délégué. Par exemple, pour rechercher le nombre de méthodes dans la liste d'invocation d'un délégué, vous pouvez écrire :  
  
 [!code-csharp[csProgGuideDelegates#29](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_9.cs)]  
  
 Les délégués ayant plusieurs méthodes dans leur liste d'invocation dérivent de <xref:System.MulticastDelegate>, qui est une sous-classe de `System.Delegate`. Le code ci-dessus fonctionne dans les deux cas, car les deux classes prennent en charge `GetInvocationList`.  
  
 Les délégués multicast sont largement utilisés dans la gestion des événements. Les objets sources d'événements envoient des notifications d'événement aux objets destinataires qui se sont inscrits pour recevoir cet événement. Pour s'inscrire à un événement, le destinataire crée une méthode conçue pour gérer l'événement, puis crée un délégué pour cette méthode et passe le délégué à la source d'événements. La source appelle le délégué quand l'événement se produit. Le délégué appelle ensuite la méthode de gestion d'événement sur le destinataire, en fournissant les données d'événement. Le type délégué d'un événement donné est défini par la source de l'événement. Pour plus d’informations, consultez [Événements](../../../csharp/programming-guide/events/index.md).  
  
 La comparaison de délégués de deux types différents assignés au moment de la compilation provoque une erreur de compilation. Si les instances de délégué sont statiquement du type `System.Delegate`, la comparaison est alors autorisée, mais retourne la valeur false à l'exécution. Exemple :  
  
 [!code-csharp[csProgGuideDelegates#30](../../../csharp/programming-guide/delegates/codesnippet/CSharp/using-delegates_10.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Délégués](../../../csharp/programming-guide/delegates/index.md)  
 [Utilisation de la variance dans les délégués](http://msdn.microsoft.com/library/e6acad03-93e0-4efb-a158-8696d5eb4ecf)  
 [Variance dans les délégués](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)  
 [Utilisation de la variance pour les délégués génériques Func et Action](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290)  
 [Événements](../../../csharp/programming-guide/events/index.md)
