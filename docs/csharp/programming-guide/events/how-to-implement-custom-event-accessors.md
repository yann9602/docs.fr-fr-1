---
title: "Comment&#160;: impl&#233;menter des accesseurs d&#39;&#233;v&#233;nement personnalis&#233;s (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "accesseurs (C#), accesseurs d'événement"
  - "add (accesseur C#)"
  - "événements (C#), add (accesseur)"
  - "événements (C#), remove (accesseur)"
  - "remove (accesseur C#)"
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 7
---
# Comment&#160;: impl&#233;menter des accesseurs d&#39;&#233;v&#233;nement personnalis&#233;s (Guide de programmation&#160;C#)
Un événement est un genre spécial de délégué multicast qui peut être appelé uniquement à partir de la classe dans laquelle il est déclaré.  Le code client s'abonne à l'événement en fournissant une référence à une méthode qui doit être appelée lorsque l'événement est déclenché.  Ces méthodes sont ajoutées à la liste d'appels du délégué à travers les accesseurs d'événement, qui ressemblent aux accesseurs de propriété mais les accesseurs d'événement sont nommés `add` et `remove`.  Dans la plupart des cas, vous ne devez pas fournir des accesseurs d'événement personnalisés.  Lorsque aucun accesseur d'événement personnalisé n'est fourni dans votre code, le compilateur les ajoute automatiquement.  Toutefois, vous devez parfois fournir le comportement personnalisé.  Ce genre de cas est illustré dans la rubrique [Comment : implémenter des événements d'interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
## Exemple  
 L'exemple suivant indique comment implémenter des accesseurs d'événement add et remove.  Bien que vous puissiez remplacer tout code à l'intérieur des accesseurs, nous vous recommandons de verrouiller l'événement précédent avant d'ajouter ou de supprimer une nouvelle méthode de gestionnaire d'événements.  
  
```  
event EventHandler IDrawingObject.OnDraw  
        {  
            add  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent += value;  
                }  
            }  
            remove  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent -= value;  
                }  
            }  
        }  
  
```  
  
## Voir aussi  
 [Événements](../../../csharp/programming-guide/events/index.md)   
 [event](../../../csharp/language-reference/keywords/event.md)