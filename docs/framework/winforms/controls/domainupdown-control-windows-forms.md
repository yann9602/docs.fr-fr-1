---
title: "DomainUpDown, contrôle (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 485640dc320809e9be5550d380b4fc9a2326e027
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="domainupdown-control-windows-forms"></a><span data-ttu-id="25ec6-102">DomainUpDown, contrôle (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="25ec6-102">DomainUpDown Control (Windows Forms)</span></span>
<span data-ttu-id="25ec6-103">Windows Forms <xref:System.Windows.Forms.DomainUpDown> contrôle ressemble à une combinaison d’une zone de texte et une paire de boutons de déplacement vers le haut ou vers le bas dans une liste.</span><span class="sxs-lookup"><span data-stu-id="25ec6-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control looks like a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="25ec6-104">Le contrôle affiche et définit une chaîne de texte à partir d’une liste de choix.</span><span class="sxs-lookup"><span data-stu-id="25ec6-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="25ec6-105">L’utilisateur peut sélectionner la chaîne en cliquant sur les boutons pour vous déplacer dans une liste de haut et bas, en appuyant sur les touches de direction haut et bas ou en tapant une chaîne qui correspond à un élément dans la liste.</span><span class="sxs-lookup"><span data-stu-id="25ec6-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="25ec6-106">Une utilisation possible de ce contrôle est pour la sélection d’éléments dans une liste triée par ordre alphabétique des noms.</span><span class="sxs-lookup"><span data-stu-id="25ec6-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span> <span data-ttu-id="25ec6-107">(Pour trier la liste, définissez la <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> propriété `true`.) La fonction de ce contrôle est très similaire à la zone de liste ou zone de liste modifiable, mais il occupe très peu d’espace.</span><span class="sxs-lookup"><span data-stu-id="25ec6-107">(To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.) The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
 <span data-ttu-id="25ec6-108">Les principales propriétés du contrôle sont <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, et <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="25ec6-108">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="25ec6-109">Le <xref:System.Windows.Forms.DomainUpDown.Items%2A> propriété contient la liste des objets dont les valeurs de texte sont affichées dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="25ec6-109">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="25ec6-110">Si <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> a la valeur `false`, le contrôle complète automatiquement le texte tapé par l’utilisateur et l’associe à une valeur dans la liste.</span><span class="sxs-lookup"><span data-stu-id="25ec6-110">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="25ec6-111">Si <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> a la valeur `true`, au-delà du dernier élément de défilement vous dirigera vers le premier élément dans la liste et vice versa.</span><span class="sxs-lookup"><span data-stu-id="25ec6-111">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="25ec6-112">Les principales méthodes du contrôle sont <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> et <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span><span class="sxs-lookup"><span data-stu-id="25ec6-112">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="25ec6-113">Ce contrôle affiche uniquement les chaînes de texte.</span><span class="sxs-lookup"><span data-stu-id="25ec6-113">This control displays only text strings.</span></span> <span data-ttu-id="25ec6-114">Si vous souhaitez un contrôle qui affiche des valeurs numériques, utilisez le <xref:System.Windows.Forms.NumericUpDown> contrôle.</span><span class="sxs-lookup"><span data-stu-id="25ec6-114">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="25ec6-115">Pour plus d’informations, consultez [contrôle NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md) .</span><span class="sxs-lookup"><span data-stu-id="25ec6-115">For more information, see [NumericUpDown Control](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md) .</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="25ec6-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="25ec6-116">In This Section</span></span>  
 [<span data-ttu-id="25ec6-117">Vue d’ensemble du contrôle DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="25ec6-117">DomainUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 <span data-ttu-id="25ec6-118">Présente les concepts généraux de le <xref:System.Windows.Forms.DomainUpDown> contrôle, ce qui permet aux utilisateurs de parcourir et sélectionner à partir d’une liste de chaînes de texte.</span><span class="sxs-lookup"><span data-stu-id="25ec6-118">Introduces the general concepts of the <xref:System.Windows.Forms.DomainUpDown> control, which allows users to browse through and select from a list of text strings.</span></span>  
  
 [<span data-ttu-id="25ec6-119">Guide pratique pour ajouter par programme des éléments aux contrôles DomainUpDown Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25ec6-119">How to: Add Items to Windows Forms DomainUpDown Controls Programmatically</span></span>](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 <span data-ttu-id="25ec6-120">Explique comment spécifier les chaînes de texte le <xref:System.Windows.Forms.DomainUpDown> contrôle doit afficher.</span><span class="sxs-lookup"><span data-stu-id="25ec6-120">Describes how to specify the text strings the <xref:System.Windows.Forms.DomainUpDown> control should display.</span></span>  
  
 [<span data-ttu-id="25ec6-121">Guide pratique pour supprimer des éléments des contrôles DomainUpDown Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25ec6-121">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 <span data-ttu-id="25ec6-122">Décrit comment supprimer des éléments à partir de la <xref:System.Windows.Forms.DomainUpDown> contrôle dans le code.</span><span class="sxs-lookup"><span data-stu-id="25ec6-122">Describes how to delete items from the <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="25ec6-123">Référence</span><span class="sxs-lookup"><span data-stu-id="25ec6-123">Reference</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <span data-ttu-id="25ec6-124">Décrit cette classe et fournit des liens vers tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="25ec6-124">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 <span data-ttu-id="25ec6-125">Décrit cette classe et propose des liens vers tous ses membres...</span><span class="sxs-lookup"><span data-stu-id="25ec6-125">Describes this class and has links to all its members..</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="25ec6-126">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="25ec6-126">Related Sections</span></span>  
 [<span data-ttu-id="25ec6-127">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="25ec6-127">Controls You Can Use On Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="25ec6-128">Fournit une liste complète de contrôles Windows Forms, avec des liens vers des informations sur leur utilisation.</span><span class="sxs-lookup"><span data-stu-id="25ec6-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>
