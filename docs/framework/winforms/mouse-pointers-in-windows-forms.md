---
title: Pointeurs de souris dans les Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aaca18bff265fafbb5bad26adfe2a8c490d85132
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="mouse-pointers-in-windows-forms"></a>Pointeurs de souris dans les Windows Forms
La souris *pointeur*, qui est parfois appelé curseur, est une bitmap qui spécifie un point de focus sur l’écran de l’utilisateur avec la souris. Cette rubrique fournit une vue d’ensemble du pointeur de la souris dans les Windows Forms et décrit quelques-unes des façons de modifier et de contrôler le pointeur de la souris.  
  
## <a name="accessing-the-mouse-pointer"></a>Le pointeur de la souris de l’accès à  
 Le pointeur de la souris est représenté par le <xref:System.Windows.Forms.Cursor> classe et chaque <xref:System.Windows.Forms.Control> a un <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> propriété qui spécifie le pointeur pour ce contrôle. Le <xref:System.Windows.Forms.Cursor> classe contient des propriétés qui décrivent le pointeur, telles que la <xref:System.Windows.Forms.Cursor.Position%2A> et <xref:System.Windows.Forms.Cursor.HotSpot%2A> propriétés et méthodes qui peuvent modifier l’apparence du pointeur, telles que la <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>, et <xref:System.Windows.Forms.Cursor.DrawStretched%2A> méthodes.  
  
## <a name="controlling-the-mouse-pointer"></a>Contrôle le pointeur de souris  
 Vous pouvez être amené à limiter la zone dans laquelle le pointeur de la souris peut être utilisé ou modifier la position de la souris. Vous pouvez obtenir ou définir l’emplacement actuel de la souris à l’aide de la <xref:System.Windows.Forms.Cursor.Position%2A> propriété de la <xref:System.Windows.Forms.Cursor>. En outre, vous pouvez limiter la zone que le pointeur de la souris peut être utilisé définir le <xref:System.Windows.Forms.Cursor.Clip%2A> propriété. Par défaut, la zone de découpage est l’ensemble de l’écran.  
  
## <a name="changing-the-mouse-pointer"></a>Modification du pointeur de la souris  
 Modification du pointeur de la souris est un moyen important de fournir des commentaires à l’utilisateur. Par exemple, le pointeur de la souris peut être modifié dans les gestionnaires de la <xref:System.Windows.Forms.Control.MouseEnter> et <xref:System.Windows.Forms.Control.MouseLeave> événements indiquer à l’utilisateur que des calculs sont en cours et pour limiter l’interaction utilisateur dans le contrôle. Parfois, le pointeur de la souris change en raison d’événements système, par exemple lorsque votre application est impliquée dans une opération de glisser-déplacer.  
  
 La principale manière de modifier le pointeur de la souris est en définissant le <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.Control.DefaultCursor%2A> propriété d’un contrôle vers un nouveau <xref:System.Windows.Forms.Cursor>. Pour obtenir des exemples de modification du pointeur de la souris, consultez l’exemple de code dans la <xref:System.Windows.Forms.Cursor> classe. En outre, le <xref:System.Windows.Forms.Cursors> classe expose un ensemble de <xref:System.Windows.Forms.Cursor> objets pour de nombreux types de pointeurs, comme un pointeur qui ressemble à une main. Pour afficher le pointeur d’attente, qui ressemble à un sablier, chaque fois que le pointeur de la souris est sur le contrôle, utilisez la <xref:System.Windows.Forms.Control.UseWaitCursor%2A> propriété de la <xref:System.Windows.Forms.Control> classe.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Cursor>  
 [Entrée de la souris dans une application Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [Fonctionnalité de glisser-déposer dans les Windows Forms](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)
