---
title: "Guide pratique pour implémenter des événements d’interface (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- interfaces [C#], event implementation in classes
- events [C#], in interfaces
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
caps.latest.revision: 21
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a780a11d8dd238187eb82933359bbb151bb3c333
ms.openlocfilehash: 4a5b5b862a88d7008049e411e6dc0f020952cc5c
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-implement-interface-events-c-programming-guide"></a>Guide pratique pour implémenter des événements d'interface (Guide de programmation C#)
Une [interface](../../../csharp/language-reference/keywords/interface.md) peut déclarer un [événement](../../../csharp/language-reference/keywords/event.md). L’exemple suivant montre comment implémenter des événements d’interface dans une classe. En gros, les règles sont les mêmes que quand vous implémentez une propriété ou une méthode d’interface.  
  
### <a name="to-implement-interface-events-in-a-class"></a>Pour implémenter des événements d’interface dans une classe  
  
-   Déclarez l’événement dans votre classe, puis appelez-le aux emplacements appropriés.  
  
    ```  
    namespace ImplementInterfaceEvents  
    {  
        public interface IDrawingObject  
        {  
            event EventHandler ShapeChanged;  
        }  
        public class MyEventArgs : EventArgs   
        {  
            // class members  
        }  
        public class Shape : IDrawingObject  
        {  
            public event EventHandler ShapeChanged;  
            void ChangeShape()  
            {  
                // Do something here before the event…  
  
                OnShapeChanged(new MyEventArgs(/*arguments*/));  
  
                // or do something here after the event.   
            }  
            protected virtual void OnShapeChanged(MyEventArgs e)  
            {  
                if(ShapeChanged != null)  
                {  
                   ShapeChanged(this, e);  
                }  
            }  
        }  
  
    }  
    ```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment gérer la situation peu courante dans laquelle votre classe hérite de plusieurs interfaces et chaque interface a un événement ayant le même nom. Dans ce cas, vous devez fournir une implémentation d’interface explicite pour au moins l’un des événements. Quand vous écrivez une implémentation d’interface explicite pour un événement, vous devez également écrire les accesseurs d’événement `add` et `remove`. Normalement, ces éléments sont fournis par le compilateur, mais dans le cas en question le compilateur ne peut pas les fournir.  
  
 En fournissant vos propres accesseurs, vous pouvez spécifier si les deux événements sont représentés par le même événement dans votre classe ou par des événements différents. Par exemple, si les événements doivent être déclenchés à des moments différents en fonction des spécifications de l’interface, vous pouvez associer chaque événement à une implémentation distincte dans votre classe. Dans l’exemple suivant, les abonnés déterminent l’événement `OnDraw` qu’il recevront en effectuant un cast de la référence de la forme en `IShape` ou `IDrawingObject`.  
  
 [!code-cs[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Événements](../../../csharp/programming-guide/events/index.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)   
 [Implémentation d’interface explicite](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)   
 [Comment : déclencher les événements de la classe de base dans les classes dérivées](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)
