---
title: "Comment : modifier la durée avant affichage du composant ToolTip Windows Forms"
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
- ToolTip component [Windows Forms], delay values
- tooltips [Windows Forms], delay values
- examples [Windows Forms], tooltips
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48bb8c08fa02a54f9bfd3febbe99f683fd68d7f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-delay-of-the-windows-forms-tooltip-component"></a>Comment : modifier la durée avant affichage du composant ToolTip Windows Forms
Il existe plusieurs valeurs de délai que vous pouvez définir pour un Windows Forms <xref:System.Windows.Forms.ToolTip> composant. L’unité de mesure pour toutes ces propriétés est millisecondes. Le <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> propriété détermine la durée pendant laquelle l’utilisateur doit pointer sur le contrôle associé pour la chaîne d’info-bulle à afficher. Le <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> propriété définit le nombre de millisecondes pour les chaînes d’info-bulle suivantes apparaissent lorsque la souris se déplace d’un contrôle d’info-bulle associé à un autre. Le <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> propriété détermine la durée pendant laquelle la chaîne d’info-bulle est affichée. Vous pouvez définir ces valeurs individuellement ou en définissant la valeur de la <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> propriété ; le délai de propriétés sont définies en fonction de la valeur affectée à la <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> propriété. Par exemple, lorsque <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> est défini sur une valeur N, <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> a la valeur N, <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> est définie à la valeur de <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> divisée par cinq (ou N/5) et <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> est défini sur une valeur qui est cinq fois la valeur de la <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> propriété (ou 5N).  
  
### <a name="to-set-the-delay"></a>Pour définir le délai d’attente  
  
1.  Définissez les propriétés suivantes comme indiqué dans cet exemple.  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du composant ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)  
 [Guide pratique pour définir des info-bulles pour les contrôles d'un Windows Form au moment du design](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [ToolTip, composant](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)
