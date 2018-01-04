---
title: "Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c4a2886dae3aee147d80957874d0d98714c0ca5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a><span data-ttu-id="c0dba-102">Utilisation d'un contrôle ComboBox Windows Forms à la place d'un contrôle ListBox</span><span class="sxs-lookup"><span data-stu-id="c0dba-102">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>
<span data-ttu-id="c0dba-103">Le <xref:System.Windows.Forms.ComboBox> et <xref:System.Windows.Forms.ListBox> contrôles ont des comportements similaires et dans certains cas interchangeables.</span><span class="sxs-lookup"><span data-stu-id="c0dba-103">The <xref:System.Windows.Forms.ComboBox> and the <xref:System.Windows.Forms.ListBox> controls have similar behaviors, and in some cases may be interchangeable.</span></span> <span data-ttu-id="c0dba-104">Il existe, toutefois, un ou l’autre est parfois plus approprié d’une tâche.</span><span class="sxs-lookup"><span data-stu-id="c0dba-104">There are times, however, when one or the other is more appropriate to a task.</span></span>  
  
 <span data-ttu-id="c0dba-105">En règle générale, une zone de liste déroulante est appropriée quand il existe une liste de choix proposés, et une zone de liste est appropriée lorsque vous souhaitez limiter l’entrée à l’élément dans la liste.</span><span class="sxs-lookup"><span data-stu-id="c0dba-105">Generally, a combo box is appropriate when there is a list of suggested choices, and a list box is appropriate when you want to limit input to what is on the list.</span></span> <span data-ttu-id="c0dba-106">Une zone de liste déroulante contient un champ de zone de texte, choix pas dans la liste peut être tapés dans.</span><span class="sxs-lookup"><span data-stu-id="c0dba-106">A combo box contains a text box field, so choices not on the list can be typed in.</span></span> <span data-ttu-id="c0dba-107">L’exception est levée quand le <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> est définie sur <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span><span class="sxs-lookup"><span data-stu-id="c0dba-107">The exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>.</span></span> <span data-ttu-id="c0dba-108">Dans ce cas, le contrôle sélectionne un élément si vous tapez sa première lettre.</span><span class="sxs-lookup"><span data-stu-id="c0dba-108">In that case, the control will select an item if you type its first letter.</span></span>  
  
 <span data-ttu-id="c0dba-109">En outre, zones de liste déroulante économiser de l’espace sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="c0dba-109">In addition, combo boxes save space on a form.</span></span> <span data-ttu-id="c0dba-110">Étant donné que la liste complète n’est pas affichée jusqu'à ce que l’utilisateur clique sur la flèche vers le bas, une zone de liste déroulante peut aisément tenir dans un petit espace où une zone de liste ne tiendrait pas.</span><span class="sxs-lookup"><span data-stu-id="c0dba-110">Because the full list is not displayed until the user clicks the down arrow, a combo box can easily fit in a small space where a list box would not fit.</span></span> <span data-ttu-id="c0dba-111">Une exception est levée quand le <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> est définie sur <xref:System.Windows.Forms.ComboBoxStyle.Simple>: la liste complète est affichée et la zone de liste déroulante occupe davantage d’espace qu’une zone de liste.</span><span class="sxs-lookup"><span data-stu-id="c0dba-111">An exception is when the <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> property is set to <xref:System.Windows.Forms.ComboBoxStyle.Simple>: the full list is displayed, and the combo box takes up more room than a list box would.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0dba-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0dba-112">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [<span data-ttu-id="c0dba-113">Guide pratique pour ajouter et supprimer des éléments d'un contrôle ComboBox, ListBox ou CheckedListBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c0dba-113">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [<span data-ttu-id="c0dba-114">Guide pratique pour trier le contenu d'un contrôle ComboBox, CheckedListBox ou ListBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c0dba-114">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [<span data-ttu-id="c0dba-115">Contrôles Windows Forms utilisés pour l’affichage de listes d’options</span><span class="sxs-lookup"><span data-stu-id="c0dba-115">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
