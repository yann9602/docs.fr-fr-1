---
title: "Comment : effectuer une liaison à une énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72439cdc1c1017378a5b6b3f6b4bf41a9eee2537
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-an-enumeration"></a><span data-ttu-id="e9357-102">Comment : effectuer une liaison à une énumération</span><span class="sxs-lookup"><span data-stu-id="e9357-102">How to: Bind to an Enumeration</span></span>
<span data-ttu-id="e9357-103">Cet exemple montre comment créer une liaison à une énumération en le liant à la méthode de GetValues de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="e9357-103">This example shows how to bind to an enumeration by binding to the enumeration's GetValues method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9357-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="e9357-104">Example</span></span>  
 <span data-ttu-id="e9357-105">Dans l’exemple suivant, la <xref:System.Windows.Controls.ListBox> affiche la liste des <xref:System.Windows.HorizontalAlignment> des valeurs d’énumération via la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="e9357-105">In the following example, the <xref:System.Windows.Controls.ListBox> displays the list of <xref:System.Windows.HorizontalAlignment> enumeration values through data binding.</span></span> <span data-ttu-id="e9357-106">Le <xref:System.Windows.Controls.ListBox> et le <xref:System.Windows.Controls.Button> sont liés par exemple que vous pouvez modifier le <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valeur de propriété de la <xref:System.Windows.Controls.Button> en sélectionnant une valeur dans la <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="e9357-106">The <xref:System.Windows.Controls.ListBox> and the <xref:System.Windows.Controls.Button> are bound such that you can change the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property value of the <xref:System.Windows.Controls.Button> by selecting a value in the <xref:System.Windows.Controls.ListBox>.</span></span>  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a><span data-ttu-id="e9357-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9357-107">See Also</span></span>  
 [<span data-ttu-id="e9357-108">Effectuer une liaison à une méthode</span><span class="sxs-lookup"><span data-stu-id="e9357-108">Bind to a Method</span></span>](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)  
 [<span data-ttu-id="e9357-109">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="e9357-109">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="e9357-110">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="e9357-110">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
