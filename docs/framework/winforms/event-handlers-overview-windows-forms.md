---
title: "Vue d'ensemble des gestionnaires d'événements (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7353f3ab4513d8331b1d38cb01ad16c7d3cde165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="event-handlers-overview-windows-forms"></a>Vue d'ensemble des gestionnaires d'événements (Windows Forms)
Un gestionnaire d’événements est une méthode qui est liée à un événement. Lorsque l’événement est déclenché, le code dans le Gestionnaire d’événements est exécuté. Chaque gestionnaire d’événements fournit deux paramètres qui vous permettent de gérer l’événement correctement. L’exemple suivant montre un gestionnaire d’événements pour un <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Click> événement.  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 Le premier paramètre,`sender`, fournit une référence à l’objet qui a déclenché l’événement. Le deuxième paramètre, `e`, dans l’exemple ci-dessus, passe un objet spécifique à l’événement qui est géré. En faisant référence à des propriétés de l’objet (et parfois ses méthodes), vous pouvez obtenir des informations telles que l’emplacement de la souris pour les événements de souris ou les données transférées dans les événements de glisser-déplacer.  
  
 En général, chaque événement produit un gestionnaire d’événements avec un type d’objet d’événement différentes pour le deuxième paramètre. Certains gestionnaires d’événements, comme celles qui concernent le <xref:System.Windows.Forms.Control.MouseDown> et <xref:System.Windows.Forms.Control.MouseUp> événements, ont le même type d’objet pour le second paramètre. Pour ces types d’événements, vous pouvez utiliser le même gestionnaire d’événements pour gérer les deux événements.  
  
 Vous pouvez également utiliser le même gestionnaire d’événements pour gérer l’événement de même pour les différents contrôles. Par exemple, si vous avez un groupe de <xref:System.Windows.Forms.RadioButton> contrôles sur un formulaire, vous pouvez créer un seul gestionnaire d’événements pour le <xref:System.Windows.Forms.Control.Click> événement et de chaque contrôle <xref:System.Windows.Forms.Control.Click> événement lié au gestionnaire d’événements unique. Pour plus d’informations, consultez [Comment : connecter plusieurs événements à un seul gestionnaire d’événements dans les Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création de gestionnaires d’événements dans les Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Vue d'ensemble des événements](../../../docs/framework/winforms/events-overview-windows-forms.md)
