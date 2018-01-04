---
title: "Comment : activer la touche TAB pour sortir d'un contrôle ToolStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], moving between
- TAB key [Windows Forms], enabling
- ToolStrip control [Windows Forms], moving from
ms.assetid: 40f9e88b-09a3-428e-8da8-c00bb65079c6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38a2e331d9530c42be6b9047b11ea235ae81d58d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-the-tab-key-to-move-out-of-a-toolstrip-control"></a>Comment : activer la touche TAB pour sortir d'un contrôle ToolStrip
Utilisez la procédure suivante pour activer l’utilisateur appuie sur la touche TAB pour passer d’un <xref:System.Windows.Forms.ToolStrip> sur le contrôle suivant dans l’ordre de tabulation.  
  
 Le <xref:System.Windows.Forms.ToolStrip> accepte la première pression sur la touche TAB et les touches flèche sélectionner des éléments dans le <xref:System.Windows.Forms.ToolStrip>. Lorsque l’utilisateur appuie sur la touche TAB une deuxième fois, il dirige l’utilisateur vers le contrôle suivant dans l’ordre de tabulation.  
  
### <a name="to-enable-the-user-to-press-the-tab-key-to-move-out-of-a-toolstrip-to-the-next-control"></a>Pour permettre à l’utilisateur d’appuyer sur la touche TAB pour sortir d’un ToolStrip au contrôle suivant  
  
-   Définir le <xref:System.Windows.Forms.ToolStrip.TabStop%2A> propriété de la <xref:System.Windows.Forms.ToolStrip> à `true`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.TabStop%2A>  
 [Vue d’ensemble du contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
