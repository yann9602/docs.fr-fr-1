---
title: "Vue d'ensemble du contrôle DomainUpDown (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5a86dc6c56c3afff8d8a3a4ca2c5d5efa8eac1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="domainupdown-control-overview-windows-forms"></a><span data-ttu-id="1f2da-102">Vue d'ensemble du contrôle DomainUpDown (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1f2da-102">DomainUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="1f2da-103">Windows Forms <xref:System.Windows.Forms.DomainUpDown> contrôle est essentiellement une combinaison d’une zone de texte et une paire de boutons de déplacement vers le haut ou vers le bas dans une liste.</span><span class="sxs-lookup"><span data-stu-id="1f2da-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control is essentially a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="1f2da-104">Le contrôle affiche et définit une chaîne de texte à partir d’une liste de choix.</span><span class="sxs-lookup"><span data-stu-id="1f2da-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="1f2da-105">L’utilisateur peut sélectionner la chaîne en cliquant sur les boutons pour vous déplacer dans une liste de haut et bas, en appuyant sur les touches de direction haut et bas ou en tapant une chaîne qui correspond à un élément dans la liste.</span><span class="sxs-lookup"><span data-stu-id="1f2da-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="1f2da-106">Une utilisation possible de ce contrôle est pour la sélection d’éléments dans une liste triée par ordre alphabétique des noms.</span><span class="sxs-lookup"><span data-stu-id="1f2da-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f2da-107">Pour trier la liste, définissez la <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="1f2da-107">To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="1f2da-108">La fonction de ce contrôle est très similaire à la zone de liste ou zone de liste modifiable, mais il occupe très peu d’espace.</span><span class="sxs-lookup"><span data-stu-id="1f2da-108">The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="1f2da-109">Propriétés de clé</span><span class="sxs-lookup"><span data-stu-id="1f2da-109">Key Properties</span></span>  
 <span data-ttu-id="1f2da-110">Les principales propriétés du contrôle sont <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, et <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f2da-110">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="1f2da-111">Le <xref:System.Windows.Forms.DomainUpDown.Items%2A> propriété contient la liste des objets dont les valeurs de texte sont affichées dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="1f2da-111">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="1f2da-112">Si <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> a la valeur `false`, le contrôle complète automatiquement le texte tapé par l’utilisateur et l’associe à une valeur dans la liste.</span><span class="sxs-lookup"><span data-stu-id="1f2da-112">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="1f2da-113">Si <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> a la valeur `true`, au-delà du dernier élément de défilement vous dirigera vers le premier élément dans la liste et vice versa.</span><span class="sxs-lookup"><span data-stu-id="1f2da-113">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="1f2da-114">Les principales méthodes du contrôle sont <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> et <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f2da-114">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="1f2da-115">Ce contrôle affiche uniquement les chaînes de texte.</span><span class="sxs-lookup"><span data-stu-id="1f2da-115">This control displays only text strings.</span></span> <span data-ttu-id="1f2da-116">Si vous souhaitez un contrôle qui affiche des valeurs numériques, utilisez le <xref:System.Windows.Forms.NumericUpDown> contrôle.</span><span class="sxs-lookup"><span data-stu-id="1f2da-116">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="1f2da-117">Pour plus d’informations, consultez [vue d’ensemble du contrôle NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1f2da-117">For more information, see [NumericUpDown Control Overview](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f2da-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f2da-118">See Also</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 [<span data-ttu-id="1f2da-119">DomainUpDown, contrôle</span><span class="sxs-lookup"><span data-stu-id="1f2da-119">DomainUpDown Control</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)
