---
title: "Comment : dimensionner un contrôle Label Windows Forms en fonction de son contenu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd89d72264e5837d2c41fcb0ab024a7b16f4205b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a><span data-ttu-id="8b3bf-102">Comment : dimensionner un contrôle Label Windows Forms en fonction de son contenu</span><span class="sxs-lookup"><span data-stu-id="8b3bf-102">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>
<span data-ttu-id="8b3bf-103">Windows Forms <xref:System.Windows.Forms.Label> contrôle peut être unique ou plusieurs lignes, et il peut être soit de taille fixe ou peut redimensionner automatiquement pour adapter sa légende.</span><span class="sxs-lookup"><span data-stu-id="8b3bf-103">The Windows Forms <xref:System.Windows.Forms.Label> control can be single-line or multi-line, and it can be either fixed in size or can automatically resize itself to accommodate its caption.</span></span> <span data-ttu-id="8b3bf-104">Le <xref:System.Windows.Forms.Label.AutoSize%2A> propriété vous permet de dimensionner les contrôles pour s’ajuster à la taille des légendes, ce qui est particulièrement utile si la changer au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="8b3bf-104">The <xref:System.Windows.Forms.Label.AutoSize%2A> property helps you size the controls to fit larger or smaller captions, which is particularly useful if the caption will change at run time.</span></span>  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a><span data-ttu-id="8b3bf-105">Pour rendre un contrôle label redimensionné dynamiquement pour s’adapter à son contenu.</span><span class="sxs-lookup"><span data-stu-id="8b3bf-105">To make a label control resize dynamically to fit its contents</span></span>  
  
1.  <span data-ttu-id="8b3bf-106">Définir son <xref:System.Windows.Forms.Label.AutoSize%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="8b3bf-106">Set its <xref:System.Windows.Forms.Label.AutoSize%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="8b3bf-107">Si <xref:System.Windows.Forms.Label.AutoSize%2A> a la valeur `false`, le texte spécifié dans le <xref:System.Windows.Forms.Label.Text%2A> propriété encapsule à la ligne suivante si possible, mais le contrôle n’augmentera pas.</span><span class="sxs-lookup"><span data-stu-id="8b3bf-107">If <xref:System.Windows.Forms.Label.AutoSize%2A> is set to `false`, the words specified in the <xref:System.Windows.Forms.Label.Text%2A> property will wrap to the next line if possible, but the control will not grow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b3bf-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b3bf-108">See Also</span></span>  
 [<span data-ttu-id="8b3bf-109">Guide pratique pour créer des touches d'accès rapide à l'aide des contrôles Label Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8b3bf-109">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [<span data-ttu-id="8b3bf-110">Vue d'ensemble du contrôle Label</span><span class="sxs-lookup"><span data-stu-id="8b3bf-110">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="8b3bf-111">Label, contrôle</span><span class="sxs-lookup"><span data-stu-id="8b3bf-111">Label Control</span></span>](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
