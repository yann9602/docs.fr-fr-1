---
title: "Comment : créer et définir un convertisseur personnalisé pour le contrôle ToolStrip dans les Windows Forms"
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
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f63ff0a7336ae80ce5652cf3e4c6c7dd409882a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a><span data-ttu-id="dc5ea-102">Comment : créer et définir un convertisseur personnalisé pour le contrôle ToolStrip dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dc5ea-102">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>
<span data-ttu-id="dc5ea-103"><xref:System.Windows.Forms.ToolStrip>contrôles permettent une prise en charge simple des thèmes et styles.</span><span class="sxs-lookup"><span data-stu-id="dc5ea-103"><xref:System.Windows.Forms.ToolStrip> controls give easy support to themes and styles.</span></span> <span data-ttu-id="dc5ea-104">Vous pouvez obtenir totalement l’aspect et le comportement (apparence) en définissant le <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> propriété ou le <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> propriété à un convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="dc5ea-104">You can achieve completely custom appearance and behavior (look and feel) by setting either the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property or the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to a custom renderer.</span></span>  
  
 <span data-ttu-id="dc5ea-105">Vous pouvez assigner des convertisseurs à chaque personne <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, ou <xref:System.Windows.Forms.StatusStrip> contrôle, ou vous pouvez utiliser la <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> affecter tous les objets en définissant le <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> propriété <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc5ea-105">You can assign renderers to each individual <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>, or <xref:System.Windows.Forms.StatusStrip> control, or you can use the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> property to affect all objects by setting the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc5ea-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A>Retourne <xref:System.Windows.Forms.ToolStripRenderMode.Custom> uniquement si la valeur de <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> n’est pas `null`.</span><span class="sxs-lookup"><span data-stu-id="dc5ea-106"><xref:System.Windows.Forms.ToolStrip.RenderMode%2A> returns <xref:System.Windows.Forms.ToolStripRenderMode.Custom> only if the value of <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> is not `null`.</span></span>  
  
### <a name="to-create-a-custom-renderer"></a><span data-ttu-id="dc5ea-107">Pour créer un convertisseur personnalisé</span><span class="sxs-lookup"><span data-stu-id="dc5ea-107">To create a custom renderer</span></span>  
  
1.  <span data-ttu-id="dc5ea-108">Étendre la <xref:System.Windows.Forms.ToolStripRenderer> classe.</span><span class="sxs-lookup"><span data-stu-id="dc5ea-108">Extend the <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span>  
  
2.  <span data-ttu-id="dc5ea-109">Implémentez le rendu personnalisé souhaité en substituant approprié *sur...*</span><span class="sxs-lookup"><span data-stu-id="dc5ea-109">Implement desired custom rendering by overriding appropriate *On…*</span></span> <span data-ttu-id="dc5ea-110">membres</span><span class="sxs-lookup"><span data-stu-id="dc5ea-110">members</span></span>  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
    ```  
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a><span data-ttu-id="dc5ea-111">Pour définir le convertisseur personnalisé pour être le rendu en cours</span><span class="sxs-lookup"><span data-stu-id="dc5ea-111">To set the custom renderer to be the current renderer</span></span>  
  
1.  <span data-ttu-id="dc5ea-112">Pour définir le convertisseur personnalisé pour un <xref:System.Windows.Forms.ToolStrip>, définissez le <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> propriété le convertisseur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="dc5ea-112">To set the custom renderer for one <xref:System.Windows.Forms.ToolStrip>, set the <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> property to the custom renderer.</span></span>  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2.  <span data-ttu-id="dc5ea-113">Ou pour définir le convertisseur personnalisé pour toutes les <xref:System.Windows.Forms.ToolStrip> classes contenues dans votre application : définir le <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> propriété au convertisseur personnalisé et affectez le <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> propriété <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span><span class="sxs-lookup"><span data-stu-id="dc5ea-113">Or to set the custom renderer for all <xref:System.Windows.Forms.ToolStrip> classes contained in your application: Set the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property to the custom renderer and set the <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> property to <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.</span></span>  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dc5ea-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc5ea-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>  
 [<span data-ttu-id="dc5ea-115">Vue d’ensemble du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dc5ea-115">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="dc5ea-116">Architecture du contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dc5ea-116">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="dc5ea-117">Résumé de la technologie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="dc5ea-117">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
