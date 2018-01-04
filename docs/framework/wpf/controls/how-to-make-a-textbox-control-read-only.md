---
title: "Comment : mettre un contrôle TextBox en lecture seule"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3d3acf1e5065633f9f4c75f24780230525b01ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-textbox-control-read-only"></a><span data-ttu-id="bb5e7-102">Comment : mettre un contrôle TextBox en lecture seule</span><span class="sxs-lookup"><span data-stu-id="bb5e7-102">How to: Make a TextBox Control Read-Only</span></span>
<span data-ttu-id="bb5e7-103">Cet exemple montre comment configurer un <xref:System.Windows.Controls.TextBox> contrôle de n’autoriser l’entrée d’utilisateur ou la modification.</span><span class="sxs-lookup"><span data-stu-id="bb5e7-103">This example shows how to configure a <xref:System.Windows.Controls.TextBox> control to not allow user input or modification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb5e7-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb5e7-104">Example</span></span>  
 <span data-ttu-id="bb5e7-105">Pour empêcher les utilisateurs de modifier le contenu d’un <xref:System.Windows.Controls.TextBox> , affectez la <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribut **true**.</span><span class="sxs-lookup"><span data-stu-id="bb5e7-105">To prevent users from modifying the contents of a <xref:System.Windows.Controls.TextBox> control, set the <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute to **true**.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <span data-ttu-id="bb5e7-106">Le <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribut affecte uniquement l’entrée d’utilisateur ; il n’affecte pas le texte dans le [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] description d’un <xref:System.Windows.Controls.TextBox> contrôle, ou le texte défini par programme via le <xref:System.Windows.Controls.TextBox.Text%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="bb5e7-106">The <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute affects user input only; it does not affect text set in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] description of a <xref:System.Windows.Controls.TextBox> control, or text set programmatically through the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="bb5e7-107">La valeur par défaut <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> est **false**.</span><span class="sxs-lookup"><span data-stu-id="bb5e7-107">The default value of <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> is **false**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb5e7-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb5e7-108">See Also</span></span>  
 [<span data-ttu-id="bb5e7-109">Vue d’ensemble de TextBox</span><span class="sxs-lookup"><span data-stu-id="bb5e7-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="bb5e7-110">Vue d’ensemble de RichTextBox</span><span class="sxs-lookup"><span data-stu-id="bb5e7-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
