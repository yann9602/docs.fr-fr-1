---
title: "Marge et marge intérieure dans les contrôles Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 22d8a73963a8f9f1e3d8b80b6c16f189e0221c55
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="9f3e5-102">Marge et marge intérieure dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f3e5-102">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="9f3e5-103">Le positionnement précis des contrôles sur votre formulaire constitue une haute priorité pour de nombreuses applications.</span><span class="sxs-lookup"><span data-stu-id="9f3e5-103">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="9f3e5-104">L'espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType> propose pour cela de nombreuses fonctionnalités de disposition.</span><span class="sxs-lookup"><span data-stu-id="9f3e5-104">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="9f3e5-105">Deux des plus importantes sont les propriétés <xref:System.Windows.Forms.Control.Margin%2A> et <xref:System.Windows.Forms.Control.Padding%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f3e5-105">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="9f3e5-106">La propriété <xref:System.Windows.Forms.Control.Margin%2A> définit l'espace autour du contrôle qui maintient les autres contrôles à une distance spécifiée des bordures du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9f3e5-106">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="9f3e5-107">La propriété <xref:System.Windows.Forms.Control.Padding%2A> définit l'espace à l'intérieur d'un contrôle qui maintient le contenu du contrôle (par exemple la valeur de sa propriété <xref:System.Windows.Forms.Control.Text%2A>) à une distance spécifiée des bordures du contrôle.</span><span class="sxs-lookup"><span data-stu-id="9f3e5-107">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="9f3e5-108">L'illustration suivante montre les propriétés <xref:System.Windows.Forms.Control.Padding%2A> et <xref:System.Windows.Forms.Control.Margin%2A> d'un contrôle.</span><span class="sxs-lookup"><span data-stu-id="9f3e5-108">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="9f3e5-109">![Remplissage et marge pour les Windows Forms contrôles](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="9f3e5-109">![Padding And Margin for Windows Forms Controls](../../../../docs/framework/winforms/controls/media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="9f3e5-110">Cette fonctionnalité est prise en charge au moment du design dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9f3e5-110">There is design-time support for this feature in Visual Studio.</span></span>  <span data-ttu-id="9f3e5-111">Consultez également [procédure pas à pas : disposition des contrôles Windows Forms avec Padding, Margins et la propriété AutoSize](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="9f3e5-111">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f3e5-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f3e5-112">See Also</span></span>  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.Control.Margin%2A>  
 <xref:System.Windows.Forms.Control.Padding%2A>  
 <xref:System.Windows.Forms.Control.LayoutEngine%2A>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
