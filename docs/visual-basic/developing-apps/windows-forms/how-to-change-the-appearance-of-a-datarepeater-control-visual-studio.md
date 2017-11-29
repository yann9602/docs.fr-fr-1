---
title: "Comment : modifier l'apparence d'un contrôle DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 585ff4c942185f3199fe6e9e47a4ebd9f1f0a478
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="01907-102">Comment : modifier l'apparence d'un contrôle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="01907-102">How to: Change the Appearance of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="01907-103">Vous pouvez modifier l’apparence d’un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle au moment du design en définissant des propriétés ou en cours d’exécution en gérant la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> événement.</span><span class="sxs-lookup"><span data-stu-id="01907-103">You can change the appearance of a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time by setting properties or at run time by handling the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event.</span></span>  
  
 <span data-ttu-id="01907-104">Les propriétés que vous définissez au moment du design lorsque la section de modèle d’élément du contrôle est sélectionnée sont répétées pour chaque <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="01907-104">Properties that you set at design time when the item template section of the control is selected will be repeated for each <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> at run time.</span></span> <span data-ttu-id="01907-105">Relatives à l’apparence des propriétés de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle proprement dit est visible au moment de l’exécution uniquement si une partie du conteneur est laissée à découvert (par exemple, si la <xref:System.Windows.Forms.Control.Padding%2A> est définie sur une valeur élevée).</span><span class="sxs-lookup"><span data-stu-id="01907-105">Appearance-related properties of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control itself will be visible at run time only if a part of the container is left uncovered (for example, if the <xref:System.Windows.Forms.Control.Padding%2A> property is set to a large value).</span></span>  
  
 <span data-ttu-id="01907-106">Au moment de l’exécution, relatives à l’apparence des propriétés peuvent être définies selon des conditions.</span><span class="sxs-lookup"><span data-stu-id="01907-106">At run time, appearance-related properties can be set based on conditions.</span></span> <span data-ttu-id="01907-107">Par exemple, dans une application de planification, vous pouvez modifier la couleur d’arrière-plan d’un élément pour avertir les utilisateurs lorsqu’un élément est en retard.</span><span class="sxs-lookup"><span data-stu-id="01907-107">For example, in a scheduling application, you might change the background color of an item to warn users when an item is past due.</span></span> <span data-ttu-id="01907-108">Dans le <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> Gestionnaire d’événements, si vous définissez une propriété dans une instruction conditionnelle, telles que `If…Then`, vous devez également utiliser un `Else` clause pour spécifier l’apparence lorsque la condition n’est pas remplie.</span><span class="sxs-lookup"><span data-stu-id="01907-108">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, if you set a property in a conditional statement such as `If…Then`, you must also use an `Else` clause to specify the appearance when the condition is not met.</span></span>  
  
### <a name="to-change-the-appearance-at-design-time"></a><span data-ttu-id="01907-109">Pour modifier l’apparence au moment du design</span><span class="sxs-lookup"><span data-stu-id="01907-109">To change the appearance at design time</span></span>  
  
1.  <span data-ttu-id="01907-110">Dans le Concepteur Windows Forms, sélectionnez la région de modèle (en haut) d’élément de la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle.</span><span class="sxs-lookup"><span data-stu-id="01907-110">In the Windows Forms Designer, select the item template (upper) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="01907-111">Dans la fenêtre Propriétés, sélectionnez une propriété et modifier la valeur.</span><span class="sxs-lookup"><span data-stu-id="01907-111">In the Properties window, select a property and change the value.</span></span> <span data-ttu-id="01907-112">Les propriétés communes qui affectent l’apparence incluent <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, et <xref:System.Windows.Forms.Control.ForeColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="01907-112">Common properties that affect appearance include <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, and <xref:System.Windows.Forms.Control.ForeColor%2A>.</span></span>  
  
### <a name="to-change-the-appearance-at-run-time"></a><span data-ttu-id="01907-113">Pour modifier l’apparence au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="01907-113">To change the appearance at run time</span></span>  
  
1.  <span data-ttu-id="01907-114">Dans l’éditeur de code, dans la liste déroulante d’événements, cliquez sur **DrawItem**.</span><span class="sxs-lookup"><span data-stu-id="01907-114">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
2.  <span data-ttu-id="01907-115">Dans la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> Gestionnaire d’événements, ajoutez le code pour définir les propriétés :</span><span class="sxs-lookup"><span data-stu-id="01907-115">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add code to set the properties:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="01907-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="01907-116">Example</span></span>  
 <span data-ttu-id="01907-117">Certaines personnalisations courantes pour la <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle comprennent l’affichage des lignes dans différentes couleurs et la modification de la couleur d’un champ selon une condition.</span><span class="sxs-lookup"><span data-stu-id="01907-117">Some common customizations for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control include displaying the rows in alternating colors and changing the color of a field based on a condition.</span></span> <span data-ttu-id="01907-118">L’exemple suivant montre comment effectuer ces personnalisations.</span><span class="sxs-lookup"><span data-stu-id="01907-118">The following example shows how to perform these customizations.</span></span> <span data-ttu-id="01907-119">Cet exemple suppose que vous avez un <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> contrôle qui est lié à la table Products dans la base de données Northwind.</span><span class="sxs-lookup"><span data-stu-id="01907-119">This example assumes that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that is bound to the Products table in the Northwind database.</span></span>  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 <span data-ttu-id="01907-120">Notez que pour les deux de ces personnalisations, vous devez fournir le code pour définir les propriétés des deux côtés de la condition.</span><span class="sxs-lookup"><span data-stu-id="01907-120">Note that for both of these customizations, you must provide code to set the properties for both sides of the condition.</span></span> <span data-ttu-id="01907-121">Si vous ne spécifiez pas le `Else` condition, vous verrez des résultats inattendus au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="01907-121">If you do not specify the `Else` condition, you will see unexpected results at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01907-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01907-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
 [<span data-ttu-id="01907-123">Introduction au contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="01907-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="01907-124">Dépannage des problèmes liés au contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="01907-124">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="01907-125">Guide pratique : afficher des données liées dans un contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="01907-125">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="01907-126">Guide pratique : afficher les contrôles indépendants dans un contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="01907-126">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="01907-127">Guide pratique : afficher des en-têtes d’élément dans un contrôle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="01907-127">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
