---
title: Constructeurs d'instances (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: efb82128ffc27a7c065d2ba12bfc08396d3b5cf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="instance-constructors-c-programming-guide"></a>Constructeurs d'instances (Guide de programmation C#)
Les constructeurs d’instances sont utilisés pour créer et initialiser toutes les variables membres d’instance quand vous utilisez l’expression [new](../../../csharp/language-reference/keywords/new.md) pour créer un objet d’une [classe](../../../csharp/language-reference/keywords/class.md). Pour initialiser une classe [statique](../../../csharp/language-reference/keywords/static.md) ou des variables statiques dans une classe non statique, vous devez définir un constructeur statique. Pour plus d’informations, consultez [Constructeurs statiques](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).  
  
 L’exemple suivant présente un constructeur d’instance :  
  
 [!code-csharp[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  Pour plus de clarté, cette classe contient des champs publics. L’utilisation de champs publics n’est pas une pratique de programmation recommandée, car elle octroie à n’importe quelle méthode n’importe où dans un programme un accès sans restriction ni vérification aux mécanismes internes d’un objet. Les données membres doivent généralement être privées et doivent être accessibles uniquement via les propriétés et les méthodes de classe.  
  
 Ce constructeur d’instance est appelé chaque fois qu’un objet basé sur la classe `CoOrds` est créé. Un constructeur comme celui-ci, qui n’accepte aucun argument, est un *constructeur par défaut*. Toutefois, il est souvent utile de fournir des constructeurs supplémentaires. Par exemple, nous pouvons ajouter un constructeur à la classe `CoOrds` qui nous permet de spécifier les valeurs initiales pour les données membres :  
  
 [!code-csharp[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 Cela permet de créer des objets `CoOrd` avec des valeurs par défaut ou initiales spécifiques, comme suit :  
  
 [!code-csharp[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 Si une classe n’a pas de constructeur, un constructeur par défaut est généré automatiquement et les valeurs par défaut sont utilisées pour initialiser les champs objet. Par exemple, [int](../../../csharp/language-reference/keywords/int.md) est initialisé à 0. Pour plus d’informations sur les valeurs par défaut, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md). Par conséquent, comme le constructeur par défaut de la classe `CoOrds` initialise toutes les données membres à zéro, il peut être supprimé entièrement sans modification du fonctionnement de la classe. Un exemple complet d’utilisation de plusieurs constructeurs est fourni dans l’exemple 1, plus loin dans cette rubrique, et un exemple d’un constructeur généré automatiquement est fourni dans l’exemple 2.  
  
 Les constructeurs d’instances peuvent également servir à appeler les constructeurs d’instances des classes de base. Le constructeur de classe peut appeler le constructeur de la classe de base via l’initialiseur, comme suit :  
  
 [!code-csharp[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 Dans cet exemple, la classe `Circle` passe des valeurs représentant le rayon et la hauteur au constructeur fourni par `Shape` duquel `Circle` est dérivé. Un exemple complet d’utilisation de `Shape` et `Circle` s’affiche dans cette rubrique en tant qu’exemple 3.  
  
## <a name="example-1"></a>Exemple 1  
 L’exemple suivant illustre une classe avec deux constructeurs de classe, l’un sans argument et l’autre avec deux arguments.  
  
 [!code-csharp[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## <a name="example-2"></a>Exemple 2  
 Dans cet exemple, la classe `Person` n’a aucun constructeur, auquel cas un constructeur par défaut est fourni automatiquement et les champs sont initialisés à leurs valeurs par défaut.  
  
 [!code-csharp[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 Notez que la valeur par défaut d’`age` est `0` et que celle de `name` est `null`. Pour plus d’informations sur les valeurs par défaut, consultez [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md).  
  
## <a name="example-3"></a>Exemple 3  
 L’exemple suivant illustre l’utilisation de l’initialiseur de classe de base. La classe `Circle` est dérivée de la classe générale `Shape` et la classe `Cylinder` est dérivée de la classe `Circle`. Le constructeur de chaque classe dérivée utilise son initialiseur de classe de base.  
  
 [!code-csharp[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 Pour obtenir d’autres exemples sur l’appel des constructeurs de classe de base, consultez [virtual](../../../csharp/language-reference/keywords/virtual.md), [override](../../../csharp/language-reference/keywords/override.md) et [base](../../../csharp/language-reference/keywords/base.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Finaliseurs](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [static](../../../csharp/language-reference/keywords/static.md)
