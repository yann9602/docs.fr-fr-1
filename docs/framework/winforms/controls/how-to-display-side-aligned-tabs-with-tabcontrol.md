---
title: "Comment : afficher des onglets alignés sur le côté à l'aide de TabControl"
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
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dcbf2cc1aee1333ad5062f2a467adfd0dbe00c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a><span data-ttu-id="85e2e-102">Comment : afficher des onglets alignés sur le côté à l'aide de TabControl</span><span class="sxs-lookup"><span data-stu-id="85e2e-102">How to: Display Side-Aligned Tabs with TabControl</span></span>
<span data-ttu-id="85e2e-103">La propriété <xref:System.Windows.Forms.TabControl.Alignment%2A> de <xref:System.Windows.Forms.TabControl> prend en charge l'affichage vertical des onglets (le long du bord gauche ou droit du contrôle), par opposition à l'affichage horizontal (en haut ou en bas du contrôle).</span><span class="sxs-lookup"><span data-stu-id="85e2e-103">The <xref:System.Windows.Forms.TabControl.Alignment%2A> property of <xref:System.Windows.Forms.TabControl> supports displaying tabs vertically (along the left or right edge of the control), as opposed to horizontally (across the top or bottom of the control).</span></span> <span data-ttu-id="85e2e-104">Par défaut, cet affichage vertical offre une expérience utilisateur médiocre, car la propriété <xref:System.Windows.Forms.TabPage.Text%2A> de l'objet <xref:System.Windows.Forms.TabPage> ne s'affiche pas dans l'onglet quand les styles visuels sont activés.</span><span class="sxs-lookup"><span data-stu-id="85e2e-104">By default, this vertical display results in a poor user experience, because the <xref:System.Windows.Forms.TabPage.Text%2A> property of the <xref:System.Windows.Forms.TabPage> object does not display in the tab when visual styles are enabled.</span></span> <span data-ttu-id="85e2e-105">De plus, il n'existe aucun moyen direct de contrôler la direction du texte dans l'onglet. Vous pouvez utiliser Owner Draw sur <xref:System.Windows.Forms.TabControl> pour améliorer cette expérience.</span><span class="sxs-lookup"><span data-stu-id="85e2e-105">There is also no direct way to control the direction of the text within the tab. You can use owner draw on <xref:System.Windows.Forms.TabControl> to improve this experience.</span></span>  
  
 <span data-ttu-id="85e2e-106">La procédure suivante montre comment afficher des onglets alignés à droite, avec le texte de l'onglet affiché de gauche à droite, à l'aide de la fonctionnalité « Owner Draw ».</span><span class="sxs-lookup"><span data-stu-id="85e2e-106">The following procedure shows how to render right-aligned tabs, with the tab text running from left to right, by using the "owner draw" feature.</span></span>  
  
### <a name="to-display-right-aligned-tabs"></a><span data-ttu-id="85e2e-107">Pour afficher des onglets alignés à droite</span><span class="sxs-lookup"><span data-stu-id="85e2e-107">To display right-aligned tabs</span></span>  
  
1.  <span data-ttu-id="85e2e-108">Ajoutez un <xref:System.Windows.Forms.TabControl> à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="85e2e-108">Add a <xref:System.Windows.Forms.TabControl> to your form.</span></span>  
  
2.  <span data-ttu-id="85e2e-109">Affectez à la propriété <xref:System.Windows.Forms.TabControl.Alignment%2A> la valeur <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="85e2e-109">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property to <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
3.  <span data-ttu-id="85e2e-110">Affectez à la propriété <xref:System.Windows.Forms.TabControl.SizeMode%2A> la valeur <xref:System.Windows.Forms.TabSizeMode.Fixed> pour que tous les onglets aient la même largeur.</span><span class="sxs-lookup"><span data-stu-id="85e2e-110">Set the <xref:System.Windows.Forms.TabControl.SizeMode%2A> property to <xref:System.Windows.Forms.TabSizeMode.Fixed>, so that all tabs are the same width.</span></span>  
  
4.  <span data-ttu-id="85e2e-111">Affectez à la propriété <xref:System.Windows.Forms.TabControl.ItemSize%2A> la taille fixe préférée pour les onglets.</span><span class="sxs-lookup"><span data-stu-id="85e2e-111">Set the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property to the preferred fixed size for the tabs.</span></span> <span data-ttu-id="85e2e-112">N'oubliez pas que la propriété <xref:System.Windows.Forms.TabControl.ItemSize%2A> se comporte comme si les onglets étaient en haut, bien qu'ils soient alignés à droite.</span><span class="sxs-lookup"><span data-stu-id="85e2e-112">Keep in mind that the <xref:System.Windows.Forms.TabControl.ItemSize%2A> property behaves as though the tabs were on top, although they are right-aligned.</span></span> <span data-ttu-id="85e2e-113">Ainsi, pour que les onglets soient plus larges vous devez modifier la propriété <xref:System.Drawing.Size.Height%2A>, et pour qu'ils soient plus hauts vous devez modifier la propriété <xref:System.Drawing.Size.Width%2A>.</span><span class="sxs-lookup"><span data-stu-id="85e2e-113">As a result, in order to make the tabs wider, you must change the <xref:System.Drawing.Size.Height%2A> property, and in order to make them taller, you must change the <xref:System.Drawing.Size.Width%2A> property.</span></span>  
  
     <span data-ttu-id="85e2e-114">Pour un résultat optimal avec l'exemple de code ci-dessous, affectez la valeur 25 à la propriété <xref:System.Drawing.Size.Width%2A> et la valeur 100 à la propriété <xref:System.Drawing.Size.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="85e2e-114">For best result with the code example below, set the <xref:System.Drawing.Size.Width%2A> of the tabs to 25 and the <xref:System.Drawing.Size.Height%2A> to 100.</span></span>  
  
5.  <span data-ttu-id="85e2e-115">Affectez à la propriété <xref:System.Windows.Forms.TabControl.DrawMode%2A> la valeur <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span><span class="sxs-lookup"><span data-stu-id="85e2e-115">Set the <xref:System.Windows.Forms.TabControl.DrawMode%2A> property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.</span></span>  
  
6.  <span data-ttu-id="85e2e-116">Définissez un gestionnaire pour l'événement <xref:System.Windows.Forms.TabControl.DrawItem> de <xref:System.Windows.Forms.TabControl> qui affiche le texte de gauche à droite.</span><span class="sxs-lookup"><span data-stu-id="85e2e-116">Define a handler for the <xref:System.Windows.Forms.TabControl.DrawItem> event of <xref:System.Windows.Forms.TabControl> that renders the text from left to right.</span></span>  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="85e2e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85e2e-117">See Also</span></span>  
 [<span data-ttu-id="85e2e-118">TabControl, contrôle</span><span class="sxs-lookup"><span data-stu-id="85e2e-118">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
