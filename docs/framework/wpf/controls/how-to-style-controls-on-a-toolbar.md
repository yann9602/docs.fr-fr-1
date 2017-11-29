---
title: "Comment : donner un style aux contrôles d'une barre d'outils"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ce090ace11262e4809dbecadd5fe89d7dfaf62e5
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-style-controls-on-a-toolbar"></a><span data-ttu-id="18eb0-102">Comment : donner un style aux contrôles d'une barre d'outils</span><span class="sxs-lookup"><span data-stu-id="18eb0-102">How to: Style Controls on a ToolBar</span></span>
<span data-ttu-id="18eb0-103">Le <xref:System.Windows.Controls.ToolBar> définit <xref:System.Windows.ResourceKey> objets pour spécifier le style des contrôles dans le <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="18eb0-103">The <xref:System.Windows.Controls.ToolBar> defines <xref:System.Windows.ResourceKey> objects to specify the style of controls within the <xref:System.Windows.Controls.ToolBar>.</span></span>  <span data-ttu-id="18eb0-104">Pour définir le style d’un contrôle dans un <xref:System.Windows.Controls.ToolBar>, définissez le `x:key` attribut de style à un <xref:System.Windows.ResourceKey> défini dans <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="18eb0-104">To style a control in a <xref:System.Windows.Controls.ToolBar>, set the `x:key` attribute of the style to a <xref:System.Windows.ResourceKey> defined in <xref:System.Windows.Controls.ToolBar>.</span></span>  
  
 <span data-ttu-id="18eb0-105">Le <xref:System.Windows.Controls.ToolBar> définit les éléments suivants <xref:System.Windows.ResourceKey> objets :</span><span class="sxs-lookup"><span data-stu-id="18eb0-105">The <xref:System.Windows.Controls.ToolBar> defines the following <xref:System.Windows.ResourceKey> objects:</span></span>  
  
-   <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a><span data-ttu-id="18eb0-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="18eb0-106">Example</span></span>  
 <span data-ttu-id="18eb0-107">L’exemple suivant définit les styles des contrôles dans un <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="18eb0-107">The following example defines styles for the controls within a <xref:System.Windows.Controls.ToolBar>.</span></span>  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a><span data-ttu-id="18eb0-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18eb0-108">See Also</span></span>  
 [<span data-ttu-id="18eb0-109">Application d’un style et création de modèles</span><span class="sxs-lookup"><span data-stu-id="18eb0-109">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
