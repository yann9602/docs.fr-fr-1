---
title: "Comment : modifier l'apparence du texte et des images de ToolStrip dans les Windows Forms"
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
- ToolStrip control [Windows Forms], appearance
- toolbars [Windows Forms], images
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], appearance
- ToolStrip control [Windows Forms], images
- ToolStrip control [Windows Forms], text
- toolbars [Windows Forms], text
ms.assetid: d62dc9d1-2edd-4dfa-aed7-1335d6e13d86
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1d926ce74db9723b6248dbb123513ca38d4adb1d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-toolstrip-text-and-images-in-windows-forms"></a><span data-ttu-id="22f91-102">Comment : modifier l'apparence du texte et des images de ToolStrip dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="22f91-102">How to: Change the Appearance of ToolStrip Text and Images in Windows Forms</span></span>
<span data-ttu-id="22f91-103">Vous pouvez contrôler si le texte et les images sont affichées sur un <xref:System.Windows.Forms.ToolStripItem> et comment ils sont alignés par rapport à l’autre et <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="22f91-103">You can control whether text and images are displayed on a <xref:System.Windows.Forms.ToolStripItem> and how they are aligned relative to each other and the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-define-what-is-displayed-on-a-toolstripitem"></a><span data-ttu-id="22f91-104">Pour définir ce qui est affiché sur un ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="22f91-104">To define what is displayed on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="22f91-105">Définir le <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> propriété la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="22f91-105">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to the desired value.</span></span> <span data-ttu-id="22f91-106">Les possibilités sont `Image`, `ImageAndText`, `None`, et `Text`.</span><span class="sxs-lookup"><span data-stu-id="22f91-106">The possibilities are `Image`, `ImageAndText`, `None`, and `Text`.</span></span> <span data-ttu-id="22f91-107">La valeur par défaut est `ImageAndText`.</span><span class="sxs-lookup"><span data-stu-id="22f91-107">The default is `ImageAndText`.</span></span>  
  
    ```vb  
    ToolStripButton2.DisplayStyle = _  
        System.Windows.Forms.ToolStripItemDisplayStyle.Image  
    ```  
  
    ```csharp  
    toolStripButton2.DisplayStyle = System.Windows.Forms.ToolStripItemDisplayStyle.Image;  
    ```  
  
### <a name="to-align-text-on-a-toolstripitem"></a><span data-ttu-id="22f91-108">Pour aligner le texte sur un ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="22f91-108">To align text on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="22f91-109">Définir le <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> propriété la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="22f91-109">Set the <xref:System.Windows.Forms.ToolStripItem.TextAlign%2A> property to the desired value.</span></span> <span data-ttu-id="22f91-110">Les possibilités sont n’importe quelle combinaison de haut, au milieu et en bas à gauche, centre et droite.</span><span class="sxs-lookup"><span data-stu-id="22f91-110">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="22f91-111">La valeur par défaut est `MiddleCenter`.</span><span class="sxs-lookup"><span data-stu-id="22f91-111">The default is `MiddleCenter`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.TextAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.TextAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-align-an-image-on-a-toolstripitem"></a><span data-ttu-id="22f91-112">Pour aligner une image sur un ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="22f91-112">To align an image on a ToolStripItem</span></span>  
  
-   <span data-ttu-id="22f91-113">Définir le <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> propriété la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="22f91-113">Set the <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A> property to the desired value.</span></span> <span data-ttu-id="22f91-114">Les possibilités sont n’importe quelle combinaison de haut, au milieu et en bas à gauche, centre et droite.</span><span class="sxs-lookup"><span data-stu-id="22f91-114">The possibilities are any combination of top, middle, and bottom with left, center, and right.</span></span> <span data-ttu-id="22f91-115">La valeur par défaut est `MiddleLeft`.</span><span class="sxs-lookup"><span data-stu-id="22f91-115">The default is `MiddleLeft`.</span></span>  
  
    ```vb  
    ToolStripSplitButton1.ImageAlign = _  
        System.Drawing.ContentAlignment.MiddleRight  
    ```  
  
    ```csharp  
    toolStripSplitButton1.ImageAlign = System.Drawing.ContentAlignment.MiddleRight;  
    ```  
  
### <a name="to-define-how-toolstripitem-text-and-images-are-displayed-relative-to-each-other"></a><span data-ttu-id="22f91-116">Pour définir l’affichent des images et du texte de ToolStripItem entre eux</span><span class="sxs-lookup"><span data-stu-id="22f91-116">To define how ToolStripItem text and images are displayed relative to each other</span></span>  
  
-   <span data-ttu-id="22f91-117">Définir le <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> propriété la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="22f91-117">Set the <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> property to the desired value.</span></span> <span data-ttu-id="22f91-118">Les possibilités sont `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, et `TextBeforeImage`.</span><span class="sxs-lookup"><span data-stu-id="22f91-118">The possibilities are `ImageAboveText`, `ImageBeforeText`, `Overlay`, `TextAboveImage`, and `TextBeforeImage`.</span></span> <span data-ttu-id="22f91-119">La valeur par défaut est `ImageBeforeText`.</span><span class="sxs-lookup"><span data-stu-id="22f91-119">The default is `ImageBeforeText`.</span></span>  
  
    ```vb  
    ToolStripButton1.TextImageRelation = _  
        System.Windows.Forms.TextImageRelation.ImageAboveText  
    ```  
  
    ```csharp  
    toolStripButton1.TextImageRelation = System.Windows.Forms.TextImageRelation.ImageAboveText;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="22f91-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22f91-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 [<span data-ttu-id="22f91-121">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="22f91-121">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="22f91-122">Architecture du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="22f91-122">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="22f91-123">Résumé de la technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="22f91-123">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
