---
title: "Comment : définir le titre d’une fenêtre à partir d’une Page"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 412771e3f43bc3755bdf9236743310ac8060165c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a><span data-ttu-id="b923f-102">Comment : définir le titre d’une fenêtre à partir d’une Page</span><span class="sxs-lookup"><span data-stu-id="b923f-102">How to: Set the Title of a Window from a Page</span></span>
<span data-ttu-id="b923f-103">Cet exemple montre comment définir le titre de la fenêtre dans laquelle un <xref:System.Windows.Controls.Page> est hébergé.</span><span class="sxs-lookup"><span data-stu-id="b923f-103">This example shows how to set the title of the window in which a <xref:System.Windows.Controls.Page> is hosted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b923f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b923f-104">Example</span></span>  
 <span data-ttu-id="b923f-105">Une page peut modifier le titre de la fenêtre qui l’héberge en définissant le <xref:System.Windows.Controls.Page.WindowTitle%2A> propriété, comme suit :</span><span class="sxs-lookup"><span data-stu-id="b923f-105">A page can change the title of the window that is hosting it by setting the <xref:System.Windows.Controls.Page.WindowTitle%2A> property, like so:</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  <span data-ttu-id="b923f-106">Définition de la <xref:System.Windows.Controls.Page.Title%2A> propriété d’une page ne modifie pas la valeur du titre de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="b923f-106">Setting the <xref:System.Windows.Controls.Page.Title%2A> property of a page does not change the value of the window title.</span></span> <span data-ttu-id="b923f-107">Au lieu de cela, <xref:System.Windows.Controls.Page.Title%2A> Spécifie le nom d’une entrée de page dans l’historique de navigation.</span><span class="sxs-lookup"><span data-stu-id="b923f-107">Instead, <xref:System.Windows.Controls.Page.Title%2A> specifies the name of a page entry in navigation history.</span></span>
