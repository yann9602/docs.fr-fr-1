---
title: "Guide pratique pour déclencher les événements de la classe de base dans les classes dérivées (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: events [C#], in derived classes
ms.assetid: 2d20556a-0aad-46fc-845e-f85d86ea617a
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c9da65958ce827fab642f4a6310d0c68dfb951a6
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-raise-base-class-events-in-derived-classes-c-programming-guide"></a>Guide pratique pour déclencher les événements de la classe de base dans les classes dérivées (Guide de programmation C#)
L’exemple suivant montre la méthode standard employée pour déclarer des événements dans une classe de base pour qu’ils puissent être déclenchés à partir de classes dérivées. Ce modèle est largement utilisé dans les classes Windows Forms de la bibliothèque de classes [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Lorsque vous créez une classe qui peut être utilisée comme classe de base pour d’autres classes, tenez compte du fait que les événements constituent un type spécial de délégué qui ne peut être appelé qu’à partir de la classe qui les a déclarés. Les classes dérivées ne peuvent pas appeler directement les événements qui sont déclarés dans la classe de base. Même si vous pouvez avoir besoin d’un événement qui ne peut être déclenché que par la classe de base, la plupart du temps, vous devez permettre à la classe dérivée d’appeler les événements de la classe de base. Pour ce faire, vous pouvez créer une méthode d’appel protégée dans la classe de base qui encapsule l’événement. En appelant ou en substituant cette méthode d’appel, les classes dérivées peuvent appeler indirectement l’événement.  
  
> [!NOTE]
>  Ne déclarez pas les événements virtuels dans une classe de base et substituez-les dans une classe dérivée. Le compilateur C# ne gère pas correctement ce type d’événement et il n’est pas possible de prévoir si un abonné de l’événement dérivé s’abonnera à l’événement de classe de base.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csProgGuideEvents#1](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-raise-base-class-events-in-derived-classes_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Événements](../../../csharp/programming-guide/events/index.md)  
 [Délégués](../../../csharp/programming-guide/delegates/index.md)  
 [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Création de gestionnaires d’événements dans les Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
