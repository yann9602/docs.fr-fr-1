---
title: "Comment : regrouper des contrôles au moyen du contrôle GroupBox Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50d29de04b4e221105bb02e58de01344f13af69f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a><span data-ttu-id="372b6-102">Comment : regrouper des contrôles au moyen du contrôle GroupBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="372b6-102">How to: Group Controls with the Windows Forms GroupBox Control</span></span>
<span data-ttu-id="372b6-103">Windows Forms <xref:System.Windows.Forms.GroupBox> contrôles sont utilisés pour regrouper d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="372b6-103">Windows Forms <xref:System.Windows.Forms.GroupBox> controls are used to group other controls.</span></span> <span data-ttu-id="372b6-104">Il existe trois raisons aux contrôles de groupe :</span><span class="sxs-lookup"><span data-stu-id="372b6-104">There are three reasons to group controls:</span></span>  
  
-   <span data-ttu-id="372b6-105">Pour créer un regroupement visuel d’éléments connexes pour une interface utilisateur claire.</span><span class="sxs-lookup"><span data-stu-id="372b6-105">To create a visual grouping of related form elements for a clear user interface.</span></span>  
  
-   <span data-ttu-id="372b6-106">Pour créer un regroupement de programmation (des cases d’option, par exemple).</span><span class="sxs-lookup"><span data-stu-id="372b6-106">To create programmatic grouping (of radio buttons, for example).</span></span>  
  
-   <span data-ttu-id="372b6-107">Pour déplacer les contrôles en tant qu’unité au moment du design.</span><span class="sxs-lookup"><span data-stu-id="372b6-107">For moving the controls as a unit at design time.</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="372b6-108">Pour créer un groupe de contrôles</span><span class="sxs-lookup"><span data-stu-id="372b6-108">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="372b6-109">Dessiner un <xref:System.Windows.Forms.GroupBox> contrôle sur un formulaire.</span><span class="sxs-lookup"><span data-stu-id="372b6-109">Draw a <xref:System.Windows.Forms.GroupBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="372b6-110">Ajouter d’autres contrôles dans la zone de groupe, en dessinant à l’intérieur de la zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="372b6-110">Add other controls to the group box, drawing each inside the group box.</span></span>  
  
     <span data-ttu-id="372b6-111">Si vous avez des contrôles existants que vous voulez inclure dans une zone de groupe, vous pouvez sélectionner tous les contrôles, les couper dans le Presse-papiers, sélectionnez le <xref:System.Windows.Forms.GroupBox> de contrôle et les coller dans la zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="372b6-111">If you have existing controls that you want to enclose in a group box, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.GroupBox> control, and then paste them into the group box.</span></span> <span data-ttu-id="372b6-112">Vous pouvez également faire glisser les dans la zone de groupe.</span><span class="sxs-lookup"><span data-stu-id="372b6-112">You can also drag them into the group box.</span></span>  
  
3.  <span data-ttu-id="372b6-113">Définir le <xref:System.Windows.Forms.GroupBox.Text%2A> propriété de la zone de groupe pour une légende appropriée.</span><span class="sxs-lookup"><span data-stu-id="372b6-113">Set the <xref:System.Windows.Forms.GroupBox.Text%2A> property of the group box to an appropriate caption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="372b6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="372b6-114">See Also</span></span>  
 <xref:System.Windows.Forms.GroupBox>  
 [<span data-ttu-id="372b6-115">GroupBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="372b6-115">GroupBox Control</span></span>](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
