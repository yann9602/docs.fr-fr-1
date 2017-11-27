---
title: "Comment : utiliser une classe de rendu des contrôles"
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
- professional appearance [Windows Forms], rendering Windows Forms controls
- visual themes [Windows Forms], applying to Windows Forms controls
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ff10cd12889750e3d32fcfce080d472f40bb9c2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-use-a-control-rendering-class"></a><span data-ttu-id="8717d-102">Comment : utiliser une classe de rendu des contrôles</span><span class="sxs-lookup"><span data-stu-id="8717d-102">How to: Use a Control Rendering Class</span></span>
<span data-ttu-id="8717d-103">Cet exemple montre comment utiliser la <xref:System.Windows.Forms.ComboBoxRenderer> classe pour restituer la flèche de déroulement d’une zone de liste déroulante contrôle de zone.</span><span class="sxs-lookup"><span data-stu-id="8717d-103">This example demonstrates how to use the <xref:System.Windows.Forms.ComboBoxRenderer> class to render the drop-down arrow of a combo box control.</span></span> <span data-ttu-id="8717d-104">L’exemple se compose de la <xref:System.Windows.Forms.Control.OnPaint%2A> méthode d’un contrôle personnalisé simple.</span><span class="sxs-lookup"><span data-stu-id="8717d-104">The example consists of the <xref:System.Windows.Forms.Control.OnPaint%2A> method of a simple custom control.</span></span> <span data-ttu-id="8717d-105">Le <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> propriété est utilisée pour déterminer si les styles visuels sont activés dans la zone cliente des fenêtres d’application.</span><span class="sxs-lookup"><span data-stu-id="8717d-105">The <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=nameWithType> property is used to determine whether visual styles are enabled in the client area of application windows.</span></span> <span data-ttu-id="8717d-106">Si les styles visuels sont actifs, puis le <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> méthode restituera la flèche de déroulement avec les styles visuels ; sinon, le <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> méthode restituera la flèche de déroulement dans le style Windows classique.</span><span class="sxs-lookup"><span data-stu-id="8717d-106">If visual styles are active, then the <xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=nameWithType> method will render the drop-down arrow with visual styles; otherwise, the <xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=nameWithType> method will render the drop-down arrow in the classic Windows style.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8717d-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="8717d-107">Example</span></span>  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8717d-108">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="8717d-108">Compiling the Code</span></span>  
 <span data-ttu-id="8717d-109">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="8717d-109">This example requires:</span></span>  
  
-   <span data-ttu-id="8717d-110">Un contrôle personnalisé dérivé de la <xref:System.Windows.Forms.Control> classe.</span><span class="sxs-lookup"><span data-stu-id="8717d-110">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
-   <span data-ttu-id="8717d-111">Un <xref:System.Windows.Forms.Form> qui héberge le contrôle personnalisé.</span><span class="sxs-lookup"><span data-stu-id="8717d-111">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
-   <span data-ttu-id="8717d-112">Les références à la <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, et <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="8717d-112">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8717d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8717d-113">See Also</span></span>  
 [<span data-ttu-id="8717d-114">Rendu des contrôles avec les styles visuels</span><span class="sxs-lookup"><span data-stu-id="8717d-114">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)
