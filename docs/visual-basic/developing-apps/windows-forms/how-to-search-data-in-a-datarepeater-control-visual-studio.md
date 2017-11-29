---
title: "Comment : rechercher des données dans un contrôle DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, implementing search
- DataRepeater, searching data
ms.assetid: a8ab5d17-b94f-43c4-8dd7-d0450226d73f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3ed7138c142a83584ecd19ccaebe0e31e421ce3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="26a04-102">Comment : rechercher des données dans un contrôle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="26a04-102">How to: Search Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="26a04-103">Lorsque vous utilisez un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle qui contient plusieurs enregistrements, vous pouvez souhaiter permettre aux utilisateurs, recherchez un enregistrement spécifique.</span><span class="sxs-lookup"><span data-stu-id="26a04-103">When you are using a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that contains many records, you may want to let users search for a specific record.</span></span> <span data-ttu-id="26a04-104">Au lieu de rechercher les données dans le contrôle lui-même, vous pouvez implémenter une recherche en interrogeant sous-jacent <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="26a04-104">Rather than searching the data in the control itself, you can implement a search by querying the underlying <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="26a04-105">Si l’élément est trouvé, vous pouvez ensuite utiliser le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> propriété pour sélectionner l’élément et de faire défiler dans l’affichage.</span><span class="sxs-lookup"><span data-stu-id="26a04-105">If the item is found, you can then use the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndex%2A> property to select the item and scroll it into view.</span></span>  
  
### <a name="to-implement-search"></a><span data-ttu-id="26a04-106">Pour implémenter la recherche</span><span class="sxs-lookup"><span data-stu-id="26a04-106">To implement search</span></span>  
  
1.  <span data-ttu-id="26a04-107">Faites glisser un contrôle <xref:System.Windows.Forms.TextBox> de la **Boîte à outils** vers le formulaire qui contient le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> .</span><span class="sxs-lookup"><span data-stu-id="26a04-107">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="26a04-108">Dans la fenêtre Propriétés, attribuez à la propriété **Name** la valeur **SearchTextBox**.</span><span class="sxs-lookup"><span data-stu-id="26a04-108">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="26a04-109">Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers le formulaire qui contient le contrôle <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> .</span><span class="sxs-lookup"><span data-stu-id="26a04-109">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="26a04-110">Dans la fenêtre Propriétés, attribuez à la propriété **Name** la valeur **SearchButton**.</span><span class="sxs-lookup"><span data-stu-id="26a04-110">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="26a04-111">Affectez à la propriété **Text** la valeur **Search**.</span><span class="sxs-lookup"><span data-stu-id="26a04-111">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="26a04-112">Double-cliquez sur le contrôle <xref:System.Windows.Forms.Button> pour ouvrir l’éditeur de code et ajoutez le code suivant au gestionnaire d’événements `SearchButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="26a04-112">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-vb[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-search-data-in-a-datarepeater-control-visual-studio_1.vb)]
     [!code-csharp[VbPowerPacksDataRepeaterSearch#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-search-data-in-a-datarepeater-control-visual-studio_1.cs)]  
  
     <span data-ttu-id="26a04-113">Remplacez *ProductsBindingSource* avec le nom de la <xref:System.Windows.Forms.BindingSource> pour votre <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>et remplacez *ProductID* avec le nom du champ que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="26a04-113">Replace *ProductsBindingSource* with the name of the <xref:System.Windows.Forms.BindingSource> for your <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, and replace *ProductID* with the name of the field that you want to search.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26a04-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26a04-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="26a04-115">Introduction au contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="26a04-115">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="26a04-116">Dépannage des problèmes liés au contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="26a04-116">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="26a04-117">Guide pratique : modifier l’apparence d’un contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="26a04-117">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
