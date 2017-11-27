---
title: "Comment : lier un ListBox à des données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: deb5e05a7c48f26d0b829ba75b4ae120841e0a80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-a-listbox-to-data"></a><span data-ttu-id="f92fa-102">Comment : lier un ListBox à des données</span><span class="sxs-lookup"><span data-stu-id="f92fa-102">How to: Bind a ListBox to Data</span></span>
<span data-ttu-id="f92fa-103">Un développeur peut créer <xref:System.Windows.Controls.ListBox> contrôles sans spécifier le contenu de chaque <xref:System.Windows.Controls.ListBoxItem> séparément.</span><span class="sxs-lookup"><span data-stu-id="f92fa-103">An application developer can create <xref:System.Windows.Controls.ListBox> controls without specifying the contents of each <xref:System.Windows.Controls.ListBoxItem> separately.</span></span> <span data-ttu-id="f92fa-104">Vous pouvez utiliser la liaison de données pour lier des données aux éléments individuels.</span><span class="sxs-lookup"><span data-stu-id="f92fa-104">You can use data binding to bind data to the individual items.</span></span>  
  
 <span data-ttu-id="f92fa-105">L’exemple suivant montre comment créer un <xref:System.Windows.Controls.ListBox> qui remplit la <xref:System.Windows.Controls.ListBoxItem> éléments de liaison de données à une source de données appelée *couleurs*.</span><span class="sxs-lookup"><span data-stu-id="f92fa-105">The following example shows how to create a <xref:System.Windows.Controls.ListBox> that populates the <xref:System.Windows.Controls.ListBoxItem> elements by data binding to a data source called *Colors*.</span></span> <span data-ttu-id="f92fa-106">Dans ce cas il n’est pas nécessaire d’utiliser <xref:System.Windows.Controls.ListBoxItem> balises pour spécifier le contenu de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="f92fa-106">In this case it is not necessary to use <xref:System.Windows.Controls.ListBoxItem> tags to specify the content of each item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f92fa-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="f92fa-107">Example</span></span>  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f92fa-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f92fa-108">See Also</span></span>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.Controls.ListBoxItem>  
 [<span data-ttu-id="f92fa-109">Contrôles</span><span class="sxs-lookup"><span data-stu-id="f92fa-109">Controls</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
