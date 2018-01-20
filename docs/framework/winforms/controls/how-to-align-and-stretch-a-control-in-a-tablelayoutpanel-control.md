---
title: "Comment : aligner et étirer un contrôle dans un contrôle TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfc1c64bc0bd9cbebad44193fb5adbe529877487
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a><span data-ttu-id="eb5c0-102">Comment : aligner et étirer un contrôle dans un contrôle TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="eb5c0-102">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>
<span data-ttu-id="eb5c0-103">Vous pouvez aligner et étirer des contrôles dans un <xref:System.Windows.Forms.TableLayoutPanel> avec la <xref:System.Windows.Forms.Control.Anchor%2A> et <xref:System.Windows.Forms.Control.Dock%2A> propriétés.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-103">You can align and stretch controls in a <xref:System.Windows.Forms.TableLayoutPanel> with the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb5c0-104">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="eb5c0-105">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="eb5c0-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="eb5c0-106">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="eb5c0-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-align-and-stretch-a-control"></a><span data-ttu-id="eb5c0-107">Pour aligner et étirer un contrôle</span><span class="sxs-lookup"><span data-stu-id="eb5c0-107">To align and stretch a control</span></span>  
  
1.  <span data-ttu-id="eb5c0-108">Faites glisser un <xref:System.Windows.Forms.TableLayoutPanel> contrôle depuis la **boîte à outils** vers votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-108">Drag a <xref:System.Windows.Forms.TableLayoutPanel> control from the **Toolbox** onto your form.</span></span>  
  
2.  <span data-ttu-id="eb5c0-109">Faites glisser un <xref:System.Windows.Forms.Button> contrôler à partir de la **boîte à outils** dans la cellule supérieure gauche de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** into the upper-left cell of the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="eb5c0-110">Le <xref:System.Windows.Forms.Button> contrôle est centré dans la cellule.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-110">The <xref:System.Windows.Forms.Button> control is centered in the cell.</span></span>  
  
3.  <span data-ttu-id="eb5c0-111">Définir la valeur de la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Anchor%2A> propriété `Left,Right`.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-111">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left,Right`.</span></span> <span data-ttu-id="eb5c0-112">Le <xref:System.Windows.Forms.Button> contrôler s’étire pour correspondre à la largeur de la cellule.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-112">The <xref:System.Windows.Forms.Button> control stretches to match the width of the cell.</span></span>  
  
4.  <span data-ttu-id="eb5c0-113">Définir la valeur de la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Anchor%2A> propriété `Top,Bottom`.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-113">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top,Bottom`.</span></span> <span data-ttu-id="eb5c0-114">Le <xref:System.Windows.Forms.Button> contrôler s’étire pour correspondre à la hauteur de la cellule.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-114">The <xref:System.Windows.Forms.Button> control stretches to match the height of the cell.</span></span>  
  
5.  <span data-ttu-id="eb5c0-115">Définir la valeur de la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-115">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="eb5c0-116">Le <xref:System.Windows.Forms.Button> contrôle se développe pour remplir la cellule.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-116">The <xref:System.Windows.Forms.Button> control expands to fill the cell.</span></span>  
  
6.  <span data-ttu-id="eb5c0-117">Définir la valeur de la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.None>.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-117">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.None>.</span></span> <span data-ttu-id="eb5c0-118">Le <xref:System.Windows.Forms.Button> contrôle retourne à sa taille d’origine et se déplace vers l’angle supérieur gauche de la cellule.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-118">The <xref:System.Windows.Forms.Button> control returns to its original size and moves to the upper-left corner of the cell.</span></span> <span data-ttu-id="eb5c0-119">Le **Concepteur Windows Forms** a défini la <xref:System.Windows.Forms.Control.Anchor%2A> propriété `Top, Left`.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-119">The **Windows Forms Designer** has set the <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span>  
  
7.  <span data-ttu-id="eb5c0-120">Définir la valeur de la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Anchor%2A> propriété `Bottom,Right`.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-120">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Bottom,Right`.</span></span> <span data-ttu-id="eb5c0-121">Le <xref:System.Windows.Forms.Button> contrôle se déplace vers l’angle inférieur droit de la cellule.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-121">The <xref:System.Windows.Forms.Button> control moves to the lower-right corner of the cell.</span></span>  
  
8.  <span data-ttu-id="eb5c0-122">Définir la valeur de la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Anchor%2A> propriété <xref:System.Windows.Forms.AnchorStyles.None>.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-122">Set the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to <xref:System.Windows.Forms.AnchorStyles.None>.</span></span> <span data-ttu-id="eb5c0-123">Le <xref:System.Windows.Forms.Button> contrôle se déplace vers le centre de la cellule.</span><span class="sxs-lookup"><span data-stu-id="eb5c0-123">The <xref:System.Windows.Forms.Button> control moves to the center of the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb5c0-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb5c0-124">See Also</span></span>  
 [<span data-ttu-id="eb5c0-125">TableLayoutPanel, contrôle</span><span class="sxs-lookup"><span data-stu-id="eb5c0-125">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
