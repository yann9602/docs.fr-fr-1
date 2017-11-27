---
title: "Vue d'ensemble du contrôle CheckBox (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CheckBox
helpviewer_keywords:
- CheckBox control [Windows Forms], about CheckBox control
- data binding [Windows Forms], checkbox controls
- check boxes [Windows Forms], about check boxes
ms.assetid: 085a4e0b-9046-473f-b141-d0edddfb2ebb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a154a3f639102e3f3e2acd62626379e12bbd1344
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="checkbox-control-overview-windows-forms"></a><span data-ttu-id="2731d-102">Vue d'ensemble du contrôle CheckBox (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2731d-102">CheckBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="2731d-103">Le contrôle <xref:System.Windows.Forms.CheckBox> Windows Forms indique si une condition particulière est activée ou désactivée.</span><span class="sxs-lookup"><span data-stu-id="2731d-103">The Windows Forms <xref:System.Windows.Forms.CheckBox> control indicates whether a particular condition is on or off.</span></span> <span data-ttu-id="2731d-104">Il est couramment utilisé pour présenter une sélection Oui/Non ou Vrai/Faux à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2731d-104">It is commonly used to present a Yes/No or True/False selection to the user.</span></span> <span data-ttu-id="2731d-105">Vous pouvez utiliser des contrôles de case à cocher dans des groupes pour afficher plusieurs choix à partir desquels l'utilisateur peut sélectionner un ou plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="2731d-105">You can use check box controls in groups to display multiple choices from which the user can select one or more.</span></span>  
  
 <span data-ttu-id="2731d-106">Le contrôle de case à cocher est similaire au contrôle de bouton radio, car chacun est utilisé pour indiquer une sélection est effectuée par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2731d-106">The check box control is similar to the radio button control in that each is used to indicate a selection that is made by the user.</span></span> <span data-ttu-id="2731d-107">Elles diffèrent dans ce qu’une case d’option dans un groupe peut être sélectionnée à la fois.</span><span class="sxs-lookup"><span data-stu-id="2731d-107">They differ in that only one radio button in a group can be selected at a time.</span></span> <span data-ttu-id="2731d-108">Avec le contrôle de case à cocher, toutefois, un nombre quelconque de cases à cocher peut être sélectionné.</span><span class="sxs-lookup"><span data-stu-id="2731d-108">With the check box control, however, any number of check boxes may be selected.</span></span>  
  
 <span data-ttu-id="2731d-109">Une case à cocher peut être connecté aux éléments d’une base de données à l’aide de la liaison de données simple.</span><span class="sxs-lookup"><span data-stu-id="2731d-109">A check box may be connected to elements in a database using simple data binding.</span></span> <span data-ttu-id="2731d-110">Plusieurs cases à cocher peuvent être regroupées à l’aide de la <xref:System.Windows.Forms.GroupBox> contrôle.</span><span class="sxs-lookup"><span data-stu-id="2731d-110">Multiple check boxes may be grouped using the <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="2731d-111">Cela est utile pour l’apparence visuelle et également pour la conception de l’interface utilisateur, dans la mesure où les contrôles groupés peuvent être déplacés ensemble dans le Concepteur de formulaires.</span><span class="sxs-lookup"><span data-stu-id="2731d-111">This is useful for visual appearance and also for user interface design, since grouped controls can be moved around together on the form designer.</span></span> <span data-ttu-id="2731d-112">Pour plus d’informations, consultez [une liaison de données Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md) et [du contrôle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="2731d-112">For more information, see [Windows Forms Data Binding](../../../../docs/framework/winforms/windows-forms-data-binding.md) and [GroupBox Control](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md).</span></span>  
  
 <span data-ttu-id="2731d-113">Le <xref:System.Windows.Forms.CheckBox> contrôle possède deux propriétés importantes, <xref:System.Windows.Forms.CheckBox.Checked%2A> et <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span><span class="sxs-lookup"><span data-stu-id="2731d-113">The <xref:System.Windows.Forms.CheckBox> control has two important properties, <xref:System.Windows.Forms.CheckBox.Checked%2A> and <xref:System.Windows.Forms.CheckBox.CheckState%2A>.</span></span> <span data-ttu-id="2731d-114">Le <xref:System.Windows.Forms.CheckBox.Checked%2A> propriété retourne `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="2731d-114">The <xref:System.Windows.Forms.CheckBox.Checked%2A> property returns either `true` or `false`.</span></span> <span data-ttu-id="2731d-115">Le <xref:System.Windows.Forms.CheckBox.CheckState%2A> propriété retourne <xref:System.Windows.Forms.CheckState.Checked> ou <xref:System.Windows.Forms.CheckState.Unchecked>; ou, si le <xref:System.Windows.Forms.CheckBox.ThreeState%2A> est définie sur `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> peut également retourner <xref:System.Windows.Forms.CheckState.Indeterminate>.</span><span class="sxs-lookup"><span data-stu-id="2731d-115">The <xref:System.Windows.Forms.CheckBox.CheckState%2A> property returns either <xref:System.Windows.Forms.CheckState.Checked> or <xref:System.Windows.Forms.CheckState.Unchecked>; or, if the <xref:System.Windows.Forms.CheckBox.ThreeState%2A> property is set to `true`, <xref:System.Windows.Forms.CheckBox.CheckState%2A> may also return <xref:System.Windows.Forms.CheckState.Indeterminate>.</span></span> <span data-ttu-id="2731d-116">Dans un état indéterminé, la zone s’affiche avec une apparence estompée pour indiquer que l’option n’est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="2731d-116">In the indeterminate state, the box is displayed with a dimmed appearance to indicate the option is unavailable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2731d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2731d-117">See Also</span></span>  
 <xref:System.Windows.Forms.CheckBox>  
 [<span data-ttu-id="2731d-118">Guide pratique pour définir des options avec les contrôles CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2731d-118">How to: Set Options with Windows Forms CheckBox Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-set-options-with-windows-forms-checkbox-controls.md)  
 [<span data-ttu-id="2731d-119">Guide pratique pour répondre à un clic du contrôle CheckBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2731d-119">How to: Respond to Windows Forms CheckBox Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [<span data-ttu-id="2731d-120">CheckBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="2731d-120">CheckBox Control</span></span>](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
