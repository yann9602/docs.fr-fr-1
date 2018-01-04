---
title: "Gestion des entrées utilisateur"
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
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0102bab4fad3b224100ae054f572d9b07102fc15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="handling-user-input"></a>Gestion des entrées utilisateur
Cette rubrique décrit les principaux événements de clavier et souris fournis par <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Lors de la gestion d’un événement, les auteurs de contrôle doivent substituer la méthode protégée `On`*EventName* au lieu d’attacher un délégué à l’événement. Pour un examen des événements, consultez [Déclenchement d’événements à partir d’un composant](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
> [!NOTE]
>  Si aucune donnée associée à un événement, une instance de la classe de base <xref:System.EventArgs> est passé comme argument à la `On` *EventName* (méthode).  
  
## <a name="keyboard-events"></a>Événements de clavier  
 Les événements de clavier courants que votre contrôle peut gérer sont <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, et <xref:System.Windows.Forms.Control.KeyUp>.  
  
|Nom de l'événement|Méthode à substituer|Description de l’événement|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Déclenché uniquement lorsque l’utilisateur appuie initialement sur une touche.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Déclenché à chaque fois que l’utilisateur appuie sur une touche. Si une touche est maintenue enfoncée, un <xref:System.Windows.Forms.Control.KeyPress> événement est déclenché à la fréquence de répétition définie par le système d’exploitation.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Déclenché lors du relâchement d’une touche.|  
  
> [!NOTE]
>  La gestion des entrées sur le clavier est considérablement plus complexe que la substitution des événements dans le tableau précédent. Ce thème dépasse le cadre de cette rubrique. Pour plus d’informations, consultez [Entrée d’utilisateur dans Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).  
  
## <a name="mouse-events"></a>Événements de souris  
 Les événements de souris que votre contrôle peut gérer sont <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, et <xref:System.Windows.Forms.Control.MouseUp>.  
  
|Nom de l'événement|Méthode à substituer|Description de l’événement|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|Déclenché quand le bouton de la souris est enfoncé alors que le pointeur se trouve sur le contrôle.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|Déclenché lorsque le pointeur pénètre la première fois dans la zone du contrôle.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|Déclenché lorsque le pointeur pointe sur le contrôle.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|Déclenché lorsque le pointeur quitte la zone du contrôle.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|Déclenché lorsque le pointeur se déplace dans la zone du contrôle.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|Déclenché lorsque le bouton de la souris est relâché alors que le pointeur se trouve sur le contrôle ou quitte la zone du contrôle.|  
  
 Le fragment de code suivant montre un exemple de substitution de la <xref:System.Windows.Forms.Control.MouseDown> événement.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 Le fragment de code suivant montre un exemple de substitution de la <xref:System.Windows.Forms.Control.MouseMove> événement.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 Le fragment de code suivant montre un exemple de substitution de la <xref:System.Windows.Forms.Control.MouseUp> événement.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 Pour obtenir le code source complet pour l’exemple `FlashTrackBar`, consultez [Comment : créer un contrôle Windows Forms qui affiche la progression](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [Définition d’un événement](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Événements](../../../../docs/standard/events/index.md)  
 [Entrées d’utilisateur dans les Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
