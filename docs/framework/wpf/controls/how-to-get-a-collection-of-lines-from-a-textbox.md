---
title: "Comment : obtenir une collection de lignes à partir d'un TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12d32266bb901f6ce47d19d92d6f0785277aa7c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a><span data-ttu-id="26482-102">Comment : obtenir une collection de lignes à partir d'un TextBox</span><span class="sxs-lookup"><span data-stu-id="26482-102">How to: Get a Collection of Lines from a TextBox</span></span>
<span data-ttu-id="26482-103">Cet exemple montre comment obtenir une collection de lignes de texte d’un <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="26482-103">This example shows how to get a collection of lines of text from a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26482-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="26482-104">Example</span></span>  
 <span data-ttu-id="26482-105">L’exemple suivant montre une méthode simple qui prend un <xref:System.Windows.Controls.TextBox> comme argument et retourne un <xref:System.Collections.Specialized.StringCollection> contenant les lignes de texte dans le **zone de texte**.</span><span class="sxs-lookup"><span data-stu-id="26482-105">The following example shows a simple method that takes a <xref:System.Windows.Controls.TextBox> as the argument, and returns a <xref:System.Collections.Specialized.StringCollection> containing the lines of text in the **TextBox**.</span></span>  <span data-ttu-id="26482-106">Le <xref:System.Windows.Controls.TextBox.LineCount%2A> propriété est utilisée pour déterminer le nombre de lignes n’est actuellement dans le **zone de texte**et le <xref:System.Windows.Controls.TextBox.GetLineText%2A> méthode est ensuite utilisée pour extraire chaque ligne et l’ajouter à la collection de lignes.</span><span class="sxs-lookup"><span data-stu-id="26482-106">The <xref:System.Windows.Controls.TextBox.LineCount%2A> property is used to determine how many lines are currently in the **TextBox**, and the <xref:System.Windows.Controls.TextBox.GetLineText%2A> method is then used to extract each line and add it to the collection of lines.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a><span data-ttu-id="26482-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26482-107">See Also</span></span>  
 [<span data-ttu-id="26482-108">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="26482-108">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="26482-109">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="26482-109">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
