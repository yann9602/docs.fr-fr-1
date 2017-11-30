---
title: "Comment : modifier la disposition d'un contrôle DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, changing layout style
- DataRepeater, changing orientation
ms.assetid: 33aa8fd5-ac63-4bd0-ba13-8c2ab17e7824
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94c5f8f5e83578ca0a82b479ef5ef359738df5f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-layout-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="585e7-102">Comment : modifier la disposition d'un contrôle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="585e7-102">How to: Change the Layout of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="585e7-103">Le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle peut être affiché dans un (éléments défilement) à la verticale ou horizontale (éléments défilement) orientation.</span><span class="sxs-lookup"><span data-stu-id="585e7-103">The <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control can be displayed in either a vertical (items scroll vertically) or horizontal (items scroll horizontally) orientation.</span></span> <span data-ttu-id="585e7-104">Vous pouvez modifier l’orientation au moment du design ou au moment de l’exécution en modifiant le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="585e7-104">You can change the orientation at design time or at run time by changing the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property.</span></span> <span data-ttu-id="585e7-105">Si vous modifiez le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriété au moment de l’exécution, vous pouvez également redimensionner la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> et repositionner les contrôles enfants.</span><span class="sxs-lookup"><span data-stu-id="585e7-105">If you change the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property at run time, you may also want to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and reposition the child controls.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="585e7-106">Si vous repositionnez des contrôles sur le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> au moment de l’exécution, vous devez appeler la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> et <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> méthodes au début et à la fin du bloc de code qui repositionne les contrôles.</span><span class="sxs-lookup"><span data-stu-id="585e7-106">If you reposition controls on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> at run time, you will need to call the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A> and <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A> methods at the beginning and end of the code block that repositions the controls.</span></span>  
  
### <a name="to-change-the-layout-at-design-time"></a><span data-ttu-id="585e7-107">Pour modifier la disposition au moment du design</span><span class="sxs-lookup"><span data-stu-id="585e7-107">To change the layout at design time</span></span>  
  
1.  <span data-ttu-id="585e7-108">Dans le Concepteur Windows Forms, sélectionnez le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle.</span><span class="sxs-lookup"><span data-stu-id="585e7-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="585e7-109">Vous devez sélectionner la bordure extérieure de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle en cliquant dans la région inférieure du contrôle, pas dans le coin supérieur <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> région.</span><span class="sxs-lookup"><span data-stu-id="585e7-109">You must select the outer border of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control by clicking in the lower region of the control, not in the upper <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> region.</span></span>  
  
2.  <span data-ttu-id="585e7-110">Dans la fenêtre Propriétés, définissez la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> propriété <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> ou <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span><span class="sxs-lookup"><span data-stu-id="585e7-110">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A> property to either <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Vertical> or <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterLayoutStyles.Horizontal>.</span></span>  
  
### <a name="to-change-the-layout-at-run-time"></a><span data-ttu-id="585e7-111">Pour modifier la disposition au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="585e7-111">To change the layout at run time</span></span>  
  
1.  <span data-ttu-id="585e7-112">Ajoutez le code suivant à un bouton ou menu `Click` Gestionnaire d’événements :</span><span class="sxs-lookup"><span data-stu-id="585e7-112">Add the following code to a button or menu `Click` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterLayout#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_1.vb)]  
  
2.  <span data-ttu-id="585e7-113">Dans la plupart des cas, vous devez ajouter du code semblable à celui indiqué dans la section exemple pour redimensionner le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> et réorganiser les contrôles pour s’ajuster à la nouvelle orientation.</span><span class="sxs-lookup"><span data-stu-id="585e7-113">In most cases, you will want to add code similar to that shown in the Example section to resize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> and rearrange controls to fit the new orientation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="585e7-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="585e7-114">Example</span></span>  
 <span data-ttu-id="585e7-115">L’exemple suivant montre comment répondre à la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> événement dans un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="585e7-115">The following example shows how to respond to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyleChanged> event in an event handler.</span></span> <span data-ttu-id="585e7-116">Cet exemple suppose que vous avez un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle nommé `DataRepeater1` sur un formulaire et que son <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> contiennent deux <xref:System.Windows.Forms.TextBox> contrôles nommés `TextBox1` et `TextBox2`.</span><span class="sxs-lookup"><span data-stu-id="585e7-116">This example requires that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control named `DataRepeater1` on a form and that its <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> contain two <xref:System.Windows.Forms.TextBox> controls named `TextBox1` and `TextBox2`.</span></span>  
  
 [!code-csharp[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.cs)]
 [!code-vb[VbPowerPacksDataRepeaterLayout#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-layout-of-a-datarepeater-control-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="585e7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="585e7-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.LayoutStyle%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.BeginResetItemTemplate%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.EndResetItemTemplate%2A>  
 [<span data-ttu-id="585e7-118">Introduction au contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="585e7-118">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="585e7-119">Dépannage des problèmes liés au contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="585e7-119">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="585e7-120">Guide pratique : modifier l’apparence d’un contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="585e7-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
