---
title: "Comment&#160;: impl&#233;menter des &#233;v&#233;nements d&#39;interface (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "événements (C#), dans les interfaces"
  - "interfaces (C#), implémentation d'événements dans des classes"
ms.assetid: 63527447-9535-4880-8e95-35e2075827df
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# Comment&#160;: impl&#233;menter des &#233;v&#233;nements d&#39;interface (Guide de programmation C#)
Une [interface](../../../csharp/language-reference/keywords/interface.md) peut déclarer un événement [](../../../csharp/language-reference/keywords/event.md "event (C# Reference)").  L'exemple suivant montre comment implémenter des événements d'interface dans une classe.  Fondamentalement, les règles sont les mêmes que lors de l'implémentation d'une propriété ou méthode d'interface.  
  
### Pour implémenter des événements d'interface dans une classe  
  
-   Déclarez l'événement dans votre classe, puis appelez\-le aux emplacements appropriés.  
  
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
  
## Exemple  
 L'exemple suivant montre comment gérer la situation la moins courante dans laquelle votre classe hérite de deux ou plusieurs interfaces et où chaque interface possède un événement avec le même nom.  Dans cette situation, vous devez fournir une implémentation d'interface explicite pour au moins l'un des événements.  Lorsque vous écrivez une implémentation d'interface explicite pour un événement, vous devez également écrire les accesseurs d'événement `add` et `remove`.  Normalement, ceux\-ci sont fournis par le compilateur, mais, dans ce cas, le compilateur ne peut pas les proposer.  
  
 En fournissant vos propres accesseurs, vous pouvez spécifier si les deux événements sont représentés par le même événement de votre classe, ou par des événements différents.  Par exemple, si les événements doivent être déclenchés à des moments différents en fonction des spécifications de l'interface, vous pouvez associer chaque événement à une implémentation distincte de votre classe.  Dans l'exemple suivant, les abonnés déterminent quel événement `OnDraw` ils reçoivent en exécutant un cast de la référence de la forme en une interface `IShape` ou `IDrawingObject`.  
  
 [!code-cs[csProgGuideEvents#10](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-implement-interface-events_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Événements](../../../csharp/programming-guide/events/index.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)   
 [Implémentation d’interface explicite](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)   
 [Comment : déclencher les événements de la classe de base dans les classes dérivées](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)