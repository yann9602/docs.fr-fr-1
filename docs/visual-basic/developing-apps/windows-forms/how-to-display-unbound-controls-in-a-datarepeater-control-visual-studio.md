---
title: "Comment : afficher les contrôles indépendants dans un contrôle DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3e96219f0ea8b8198967e9fa3c6e5afb824352db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="130fe-102">Comment : afficher les contrôles indépendants dans un contrôle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="130fe-102">How to: Display Unbound Controls in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="130fe-103">En plus de contrôles dépendants, vous voudrez ajouter d’autres contrôles à un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, tel qu’une étiquette statique ou une image qui est répétée sur chaque élément dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle.</span><span class="sxs-lookup"><span data-stu-id="130fe-103">In addition to bound controls, you may want to add other controls to a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="130fe-104">Vous devez également disposer au moins un contrôle lié sur le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ou rien ne s’affichera au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="130fe-104">You must also have at least one bound control on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> or nothing will be displayed at run time.</span></span>  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a><span data-ttu-id="130fe-105">Pour ajouter des contrôles indépendants à un contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="130fe-105">To add unbound controls to a DataRepeater</span></span>  
  
1.  <span data-ttu-id="130fe-106">Faites glisser un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôler à partir de la **Visual Basic PowerPacks** onglet dans le **boîte à outils** à un contrôle de formulaire ou un conteneur.</span><span class="sxs-lookup"><span data-stu-id="130fe-106">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="130fe-107">Faites glisser les poignées de dimensionnement et de déplacement pour dimensionner et positionner le contrôle.</span><span class="sxs-lookup"><span data-stu-id="130fe-107">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="130fe-108">Vous pouvez également redimensionner et positionner le contrôle en modifiant le **taille** et **Position** propriétés dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="130fe-108">You can also size and position the control by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="130fe-109">Ajoutez au moins un contrôle lié aux données à le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle.</span><span class="sxs-lookup"><span data-stu-id="130fe-109">Add at least one data-bound control to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="130fe-110">Pour plus d’informations, consultez [Comment : afficher les données liées dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="130fe-110">For more information, see [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
4.  <span data-ttu-id="130fe-111">Faites glisser un contrôle de la **boîte à outils** sur la région de modèle d’élément de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle.</span><span class="sxs-lookup"><span data-stu-id="130fe-111">Drag a control from the **Toolbox** onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="130fe-112">Notez que le contrôle possède deux régions rectangulaires.</span><span class="sxs-lookup"><span data-stu-id="130fe-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="130fe-113">La région interne est la *modèle d’élément*; les contrôles ajoutés au modèle seront répétés dans chaque élément dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="130fe-113">The inner region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="130fe-114">La région externe est la *la fenêtre d’affichage*, où les éléments seront affiche ; les contrôles qui sont ajoutés à cette région ne s’affichera pas en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="130fe-114">The outer region is the *viewport*, where the items will be displayed; controls that are added to this region will not be displayed at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="130fe-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="130fe-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="130fe-116">Introduction au contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="130fe-116">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="130fe-117">Dépannage des problèmes liés au contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="130fe-117">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="130fe-118">Guide pratique : afficher des données liées dans un contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="130fe-118">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="130fe-119">Comment : créer un formulaire maître/détail en utilisant deux contrôles DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="130fe-119">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="130fe-120">Guide pratique : modifier l’apparence d’un contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="130fe-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
