---
title: "Guide pratique pour publier des événements conformes aux indications du .NET Framework (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 78d069249c8131a091a206703c475faaf641d17b
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Guide pratique pour publier des événements conformes aux indications du .NET Framework (Guide de programmation C#)
La procédure suivante montre comment ajouter à vos classes et structures des événements qui respectent le modèle [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] standard. Tous les événements dans la bibliothèque de classes [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] sont basés sur le délégué <xref:System.EventHandler>, qui est défini comme suit :  
  
```  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  Le [!INCLUDE[dnprdnlong](../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] introduit une version générique de ce délégué, <xref:System.EventHandler%601>. Les exemples suivants montrent comment utiliser les deux versions.  
  
 Bien que les événements dans les classes que vous définissez puissent être basés sur n’importe quel type délégué valide, même les délégués qui retournent une valeur, il est généralement recommandé de baser les événements sur le modèle [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] à l’aide de <xref:System.EventHandler>, comme illustré dans l’exemple suivant.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Pour publier des événements basés sur le modèle EventHandler  
  
1.  (Ignorez cette étape et passez à l’étape 3a si vous n’avez pas à envoyer de données personnalisées avec votre événement.) Déclarez la classe pour vos données personnalisées avec une étendue visible par vos classes de serveur de publication et d’abonné. Ajoutez ensuite les membres nécessaires pour contenir vos données d’événement personnalisées. Dans cet exemple, une simple chaîne est retournée.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
2.  (Ignorez cette étape si vous utilisez la version générique de <xref:System.EventHandler%601>.) Déclarez un délégué dans votre classe de publication. Donnez-lui un nom qui se termine par *EventHandler*. Le deuxième paramètre spécifie votre type EventArgs personnalisé.  
  
    ```  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  Déclarez l’événement dans votre classe de publication en effectuant l’une des étapes suivantes.  
  
    1.  Si vous n’avez aucune classe EventArgs personnalisée, votre type d’événement sera le délégué EventHandler non générique. Il est inutile de déclarer le délégué, car il est déjà déclaré dans l’espace de noms <xref:System> inclus quand vous créez votre projet C#. Ajoutez le code suivant à votre classe de serveur de publication.  
  
        ```  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  Si vous utilisez la version non générique de <xref:System.EventHandler> et que vous avez une classe personnalisée dérivée de <xref:System.EventArgs>, déclarez votre événement à l’intérieur de votre classe de publication et utilisez votre délégué de l’étape 2 comme type.  
  
        ```  
        public event CustomEventHandler RaiseCustomEvent;  
  
        ```  
  
    3.  Si vous utilisez la version générique, vous n’avez pas besoin de délégué personnalisé. Au lieu de cela, dans votre classe de publication, vous spécifiez votre type d’événement en tant que `EventHandler<CustomEventArgs>`, en insérant le nom de votre propre classe entre les crochets.  
  
        ```  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre les étapes précédentes avec une classe EventArgs personnalisée et <xref:System.EventHandler%601> comme type d’événement.  
  
 [!code-cs[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Delegate>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Événements](../../../csharp/programming-guide/events/index.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)
