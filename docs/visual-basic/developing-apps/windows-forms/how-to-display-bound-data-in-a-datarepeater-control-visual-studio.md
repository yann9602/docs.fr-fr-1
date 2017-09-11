---
title: "Comment : afficher des données liées dans un contrôle DataRepeater (Visual Studio) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 677c964ee9ebbad6ec712a29c8b9c8920aa7e7ec
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="5785e-102">Comment : afficher des données liées dans un contrôle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="5785e-102">How to: Display Bound Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="5785e-103">L’utilisation la plus courante de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle consiste à afficher des données liées à partir d’une base de données ou autre source de données.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="5785e-103">The most common use of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control is to display bound data from a database or other data source.</span></span>  
  
 <span data-ttu-id="5785e-104">En plus des contrôles dépendants, vous pouvez souhaiter ajouter d’autres contrôles, par exemple une étiquette statique ou une image répétée sur chaque élément de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="5785e-104">In addition to bound controls, you may want to add other controls, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="5785e-105">Pour plus d’informations, consultez [Comment : afficher des contrôles indépendants dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="5785e-105">For more information, see [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
 <span data-ttu-id="5785e-106">Vous pouvez également lier à une source de données au moment de l’exécution en définissant le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>propriété `True` et en assignant une source de données pour le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A>propriété.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> </xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A></span><span class="sxs-lookup"><span data-stu-id="5785e-106">You can also bind to a data source at run time by setting the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> property to `True` and assigning a data source to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> property.</span></span> <span data-ttu-id="5785e-107">Dans ce cas, vous devrez gérer l’interaction avec la source de données.</span><span class="sxs-lookup"><span data-stu-id="5785e-107">In this case, you will need to manage all interaction with the data source.</span></span> <span data-ttu-id="5785e-108">Pour plus d’informations, consultez [Mode virtuel dans le contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="5785e-108">For more information, see [Virtual Mode in the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a><span data-ttu-id="5785e-109">Pour créer un DataRepeater lié aux données</span><span class="sxs-lookup"><span data-stu-id="5785e-109">To create a data-bound DataRepeater</span></span>  
  
1.  <span data-ttu-id="5785e-110">Faites glisser un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôler à partir de la **Visual Basic PowerPacks** onglet le **boîte à outils** à un formulaire ou un contrôle conteneur.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="5785e-110">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="5785e-111">Faites glisser les poignées de dimensionnement et de déplacement pour redimensionner et positionner le contrôle.</span><span class="sxs-lookup"><span data-stu-id="5785e-111">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="5785e-112">Notez que le contrôle possède deux régions rectangulaires.</span><span class="sxs-lookup"><span data-stu-id="5785e-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="5785e-113">La région supérieure est la *modèle d’élément*; les contrôles ajoutés au modèle seront répétés dans chaque élément dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle au moment de l’exécution.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="5785e-113">The upper region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="5785e-114">La région inférieure est la *viewport*, où les éléments seront affiche.</span><span class="sxs-lookup"><span data-stu-id="5785e-114">The lower region is the *viewport*, where the items will be displayed.</span></span>  
  
     <span data-ttu-id="5785e-115">Vous pouvez également redimensionner et positionner le contrôle ou le modèle d’élément en modifiant le **taille** et **Position** propriétés dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="5785e-115">You can also size and position the control or the item template by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="5785e-116">Dans le menu **Données** , cliquez sur **Afficher les sources de données**.</span><span class="sxs-lookup"><span data-stu-id="5785e-116">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5785e-117">Si le **des Sources de données** fenêtre est vide, ajoutez une source de données à celle-ci.</span><span class="sxs-lookup"><span data-stu-id="5785e-117">If the **Data Sources** window is empty, add a data source to it.</span></span> <span data-ttu-id="5785e-118">Pour plus d’informations, consultez [ajouter de nouvelles sources de données](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).</span><span class="sxs-lookup"><span data-stu-id="5785e-118">For more information, see [Add new data sources](https://docs.microsoft.com/visualstudio/data-tools/add-new-data-sources).</span></span>  
  
4.  <span data-ttu-id="5785e-119">Dans le **des Sources de données** fenêtre, sélectionnez le nœud de niveau supérieur pour la table qui contient les données que vous souhaitez lier.</span><span class="sxs-lookup"><span data-stu-id="5785e-119">In the **Data Sources** window, select the top-level node for the table that contains the data that you want to bind.</span></span>  
  
5.  <span data-ttu-id="5785e-120">Modifier le type de déplacement de la table à `Details` en cliquant sur `Details` dans la liste déroulante du nœud table.</span><span class="sxs-lookup"><span data-stu-id="5785e-120">Change the drop type of the table to `Details` by clicking `Details` in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="5785e-121">Sélectionnez le nœud table et faites-le glisser sur la région de modèle d’élément de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>contrôle.</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="5785e-121">Select the table node and drag it onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="5785e-122">Vous pouvez spécifier des types de contrôles sont affichés pour chaque champ.</span><span class="sxs-lookup"><span data-stu-id="5785e-122">You can specify which types of controls are displayed for each field.</span></span> <span data-ttu-id="5785e-123">Pour plus d’informations, consultez [définir le contrôle à créer lors du déplacement de la fenêtre Sources de données](https://docs.microsoft.com/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).</span><span class="sxs-lookup"><span data-stu-id="5785e-123">For more information, see [Set the control to be created when dragging from the Data Sources window](https://docs.microsoft.com/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5785e-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5785e-124">See Also</span></span>  
 <span data-ttu-id="5785e-125"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span><span class="sxs-lookup"><span data-stu-id="5785e-125"><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater></span></span>   
<span data-ttu-id="5785e-126"> [Introduction au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="5785e-126"> [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="5785e-127"> [Comment : afficher les contrôles indépendants dans un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="5785e-127"> [How to: Display Unbound Controls in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="5785e-128"> [Comment : créer un formulaire maître/détail en utilisant deux contrôles DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md) </span><span class="sxs-lookup"><span data-stu-id="5785e-128"> [How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md) </span></span>  
<span data-ttu-id="5785e-129"> [Comment : modifier l’apparence d’un contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span><span class="sxs-lookup"><span data-stu-id="5785e-129"> [How to: Change the Appearance of a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md) </span></span>  
<span data-ttu-id="5785e-130"> [Dépannage des problèmes liés au contrôle DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="5785e-130"> [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)</span></span>
