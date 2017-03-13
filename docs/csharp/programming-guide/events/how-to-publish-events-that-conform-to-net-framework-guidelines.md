---
title: "Comment&#160;: publier des &#233;v&#233;nements conformes aux indications du .NET&#160;Framework (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "événements (C#), instructions d'implémentation"
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# Comment&#160;: publier des &#233;v&#233;nements conformes aux indications du .NET&#160;Framework (Guide de programmation C#)
La procédure suivante montre comment ajouter des événements qui suivent le modèle standard du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] à vos classes et structures.  Tous les événements de la bibliothèque de classes du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] sont basés sur le délégué <xref:System.EventHandler>, défini comme suit :  
  
```  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  Le [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong-md.md)] introduit une version générique de ce délégué, <xref:System.EventHandler%601>.  Les exemples suivants montrent comment utiliser les deux versions.  
  
 Bien que les événements des classes que vous définissez puissent être basés sur tout type délégué valide, y compris les délégués qui retournent une valeur, il est généralement recommandé de baser les événements sur le modèle du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] en utilisant <xref:System.EventHandler>, comme illustré dans l'exemple suivant.  
  
### Pour publier les événements basés sur le modèle EventHandler  
  
1.  \(Passez directement à l'étape 3a si vous n'avez pas besoin d'envoyer des données personnalisées avec votre événement.\) Déclarez la classe pour vos données personnalisées avec une portée visible des classes d'éditeur et d'abonné.  Ajoutez ensuite les membres requis pour conserver vos données d'événement personnalisées.  Dans cet exemple, une simple chaîne est retournée.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
2.  \(Ignorez cette étape si vous utilisez la version générique de <xref:System.EventHandler%601>.\) Déclarez un délégué dans votre classe d'édition.  Donnez\-lui un nom qui se termine par *EventHandler*.  Le deuxième paramètre spécifie votre type EventArgs personnalisé.  
  
    ```  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  Déclarez l'événement dans votre classe d'édition en utilisant l'une des étapes ci\-après.  
  
    1.  Si vous n'avez aucune classe EventArgs personnalisée, votre type d'événement est le délégué EventHandler non générique.  Vous n'avez pas besoin de déclarer le délégué parce qu'il l'est déjà dans l'espace de noms <xref:System> inclus lors de la création de votre projet C\# :  Ajoutez le code suivant à votre classe d'éditeur.  
  
        ```  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  Si vous utilisez la version non générique de <xref:System.EventHandler> et que vous avez une classe personnalisée dérivée de <xref:System.EventArgs>, déclarez votre événement à l'intérieur de votre classe d'édition et utilisez le délégué de l'étape 2 comme type.  
  
        ```  
        public event CustomEventHandler RaiseCustomEvent;  
  
        ```  
  
    3.  Si vous utilisez la version générique, vous n'avez pas besoin d'un délégué personnalisé.  À la place, dans votre classe d'édition, vous spécifiez votre type d'événement comme `EventHandler<CustomEventArgs>`, en substituant le nom de votre propre classe entre les signes « inférieur à » et « supérieur à ».  
  
        ```  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## Exemple  
 L'exemple suivant illustre les étapes précédentes en utilisant une classe EventArgs personnalisée et <xref:System.EventHandler%601> comme type d'événement.  
  
 [!code-cs[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## Voir aussi  
 <xref:System.Delegate>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Événements](../../../csharp/programming-guide/events/index.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)