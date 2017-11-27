---
title: Vue d'ensemble du composant ToolTip (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff2364b5c7223c265571257920a7c7e794b4921b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-component-overview-windows-forms"></a><span data-ttu-id="0af76-102">Vue d'ensemble du composant ToolTip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0af76-102">ToolTip Component Overview (Windows Forms)</span></span>
<span data-ttu-id="0af76-103">Le composant Windows Forms <xref:System.Windows.Forms.ToolTip> affiche du texte quand l'utilisateur pointe sur des contrôles.</span><span class="sxs-lookup"><span data-stu-id="0af76-103">The Windows Forms <xref:System.Windows.Forms.ToolTip> component displays text when the user points at controls.</span></span> <span data-ttu-id="0af76-104">Une info-bulle peut être associée à n'importe quel contrôle.</span><span class="sxs-lookup"><span data-stu-id="0af76-104">A ToolTip can be associated with any control.</span></span> <span data-ttu-id="0af76-105">Un exemple d’utilisation de ce composant : pour économiser de l’espace sur un formulaire, vous pouvez afficher une petite icône sur un bouton et utiliser une info-bulle pour expliquer la fonction du bouton.</span><span class="sxs-lookup"><span data-stu-id="0af76-105">An example use of this component: to save space on a form, you can display a small icon on a button and use a ToolTip to explain the button's function.</span></span>  
  
## <a name="working-with-the-tooltip-component"></a><span data-ttu-id="0af76-106">Utilisation du composant ToolTip</span><span class="sxs-lookup"><span data-stu-id="0af76-106">Working with the ToolTip Component</span></span>  
 <span data-ttu-id="0af76-107">A <xref:System.Windows.Forms.ToolTip> composant fournit un `ToolTip` propriété à plusieurs contrôles sur un Windows Form ou autre conteneur.</span><span class="sxs-lookup"><span data-stu-id="0af76-107">A <xref:System.Windows.Forms.ToolTip> component provides a `ToolTip` property to multiple controls on a Windows Form or other container.</span></span> <span data-ttu-id="0af76-108">Par exemple, si vous placez un <xref:System.Windows.Forms.ToolTip> composant d’un formulaire, vous pouvez afficher la « Type de votre nom ici » pour un <xref:System.Windows.Forms.TextBox> contrôler et « Cliquez ici pour enregistrer les modifications » pour un <xref:System.Windows.Forms.Button> contrôle.</span><span class="sxs-lookup"><span data-stu-id="0af76-108">For example, if you place one <xref:System.Windows.Forms.ToolTip> component on a form, you can display "Type your name here" for a <xref:System.Windows.Forms.TextBox> control and "Click here to save changes" for a <xref:System.Windows.Forms.Button> control.</span></span>  
  
 <span data-ttu-id="0af76-109">Les méthodes clés de la <xref:System.Windows.Forms.ToolTip> composant sont <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> et <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.</span><span class="sxs-lookup"><span data-stu-id="0af76-109">The key methods of the <xref:System.Windows.Forms.ToolTip> component are <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> and <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.</span></span> <span data-ttu-id="0af76-110">Vous pouvez utiliser la <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> pour définir les info-bulles affichées pour des contrôles.</span><span class="sxs-lookup"><span data-stu-id="0af76-110">You can use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method to set the ToolTips displayed for controls.</span></span> <span data-ttu-id="0af76-111">Pour plus d’informations, consultez [Comment : définir des info-bulles pour les contrôles sur un Windows Form au moment du Design](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="0af76-111">For more information, see [How to: Set ToolTips for Controls on a Windows Form at Design Time](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).</span></span> <span data-ttu-id="0af76-112">Les propriétés de clé sont <xref:System.Windows.Forms.ToolTip.Active%2A>, qui doit être défini sur `true` pour l’info-bulle s’affiche, et <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, qui définit la durée pendant laquelle la chaîne d’info-bulle est affichée, la durée pendant laquelle l’utilisateur doit pointer sur le contrôle de l’info-bulle s’affiche et la durée de l’opération prend pour les info-bulles suivantes pour s’affichent.</span><span class="sxs-lookup"><span data-stu-id="0af76-112">The key properties are <xref:System.Windows.Forms.ToolTip.Active%2A>, which must be set to `true` for the ToolTip to appear, and <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, which sets the length of time that the ToolTip string is shown, how long the user must point at the control for the ToolTip to appear, and how long it takes for subsequent ToolTip windows to appear.</span></span> <span data-ttu-id="0af76-113">Pour plus d’informations, consultez [Comment : modifier la durée avant affichage du composant ToolTip Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).</span><span class="sxs-lookup"><span data-stu-id="0af76-113">For more information, see [How to: Change the Delay of the Windows Forms ToolTip Component](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af76-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0af76-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolTip>  
 [<span data-ttu-id="0af76-115">Guide pratique pour définir des info-bulles pour les contrôles d'un Windows Form au moment du design</span><span class="sxs-lookup"><span data-stu-id="0af76-115">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [<span data-ttu-id="0af76-116">Guide pratique pour modifier la durée avant affichage du composant ToolTip Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0af76-116">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
