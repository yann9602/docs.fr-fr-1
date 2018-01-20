---
title: "Comment : désigner un bouton Windows Forms comme bouton Annuler à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 30e77d9c-d565-4ab5-a84a-62c043af8822
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0772fd01c2431df3b3aea034616913bd44dc0f05
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button-using-the-designer"></a><span data-ttu-id="49985-102">Comment : désigner un bouton Windows Forms comme bouton Annuler à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="49985-102">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>
<span data-ttu-id="49985-103">Sur un Windows Form, vous pouvez désigner un <xref:System.Windows.Forms.Button> contrôle soit le bouton Annuler.</span><span class="sxs-lookup"><span data-stu-id="49985-103">On any Windows Form, you can designate a <xref:System.Windows.Forms.Button> control to be the cancel button.</span></span> <span data-ttu-id="49985-104">Un bouton cancel chaque fois que l’utilisateur appuie sur la touche ÉCHAP, quels que soient les autres contrôles du formulaire a le focus.</span><span class="sxs-lookup"><span data-stu-id="49985-104">A cancel button is clicked whenever the user presses the ESC key, regardless of which other control on the form has the focus.</span></span> <span data-ttu-id="49985-105">Ce bouton est généralement programmé pour permettre à l’utilisateur de quitter rapidement une opération sans valider aucune action.</span><span class="sxs-lookup"><span data-stu-id="49985-105">Such a button is usually programmed to enable the user to quickly exit an operation without committing to any action.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="49985-106">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="49985-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="49985-107">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="49985-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="49985-108">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="49985-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-designate-the-cancel-button"></a><span data-ttu-id="49985-109">Pour désigner le bouton Annuler</span><span class="sxs-lookup"><span data-stu-id="49985-109">To designate the cancel button</span></span>  
  
1.  <span data-ttu-id="49985-110">Sélectionnez le formulaire sur lequel se trouve le bouton.</span><span class="sxs-lookup"><span data-stu-id="49985-110">Select the form on which the button resides.</span></span>  
  
2.  <span data-ttu-id="49985-111">Dans le **propriétés** , configurez du formulaire <xref:System.Windows.Forms.Form.CancelButton%2A> propriété le <xref:System.Windows.Forms.Button> nom du contrôle.</span><span class="sxs-lookup"><span data-stu-id="49985-111">In the **Properties** window, set the form's <xref:System.Windows.Forms.Form.CancelButton%2A> property to the <xref:System.Windows.Forms.Button> control's name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49985-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="49985-112">See Also</span></span>  
 <xref:System.Windows.Forms.Form.CancelButton%2A>  
 [<span data-ttu-id="49985-113">Vue d'ensemble du contrôle Button</span><span class="sxs-lookup"><span data-stu-id="49985-113">Button Control Overview</span></span>](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [<span data-ttu-id="49985-114">Méthodes de sélection du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49985-114">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="49985-115">Guide pratique pour répondre à un clic du contrôle Button Windows Forms</span><span class="sxs-lookup"><span data-stu-id="49985-115">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="49985-116">Guide pratique pour désigner un bouton Windows Forms comme bouton Accepter à l’aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="49985-116">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [<span data-ttu-id="49985-117">Button, contrôle</span><span class="sxs-lookup"><span data-stu-id="49985-117">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
