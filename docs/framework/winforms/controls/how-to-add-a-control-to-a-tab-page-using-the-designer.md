---
title: "Comment : ajouter un contrôle à une page d'onglet à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TabPage control
- tab controls [Windows Forms], tab order
- tab pages [Windows Forms], adding controls
ms.assetid: 7ee734e1-e31e-4ed0-bbc0-a7e8a1f20fef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5be65fc562d5b4d80a57ab068d97d66ccb17b6e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-control-to-a-tab-page-using-the-designer"></a><span data-ttu-id="c77c5-102">Comment : ajouter un contrôle à une page d'onglet à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="c77c5-102">How to: Add a Control to a Tab Page Using the Designer</span></span>
<span data-ttu-id="c77c5-103">L’utilisation de Windows Forms <xref:System.Windows.Forms.TabControl> consiste à afficher d’autres contrôles dans une structure organisée.</span><span class="sxs-lookup"><span data-stu-id="c77c5-103">The use of the Windows Forms <xref:System.Windows.Forms.TabControl> is to display other controls in an organized fashion.</span></span> <span data-ttu-id="c77c5-104">Vous pouvez utiliser ces instructions pour afficher une image dans la partie principale d’une page d’onglet.</span><span class="sxs-lookup"><span data-stu-id="c77c5-104">You can use these instructions to display a picture on the main part of a tab page.</span></span> <span data-ttu-id="c77c5-105">Pour plus d’informations sur l’ajout d’une icône à la partie de l’étiquette d’une page d’onglet, consultez [Comment : modifier l’apparence du contrôle TabControl Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span><span class="sxs-lookup"><span data-stu-id="c77c5-105">For information about adding an icon to the label part of a tab page, see [How to: Change the Appearance of the Windows Forms TabControl](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md).</span></span>  
  
 <span data-ttu-id="c77c5-106">La procédure suivante requiert un **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.TabControl> contrôle.</span><span class="sxs-lookup"><span data-stu-id="c77c5-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="c77c5-107">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c77c5-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c77c5-108">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="c77c5-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c77c5-109">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="c77c5-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c77c5-110">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="c77c5-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-a-control-using-the-designer"></a><span data-ttu-id="c77c5-111">Pour ajouter un contrôle à l’aide du Concepteur</span><span class="sxs-lookup"><span data-stu-id="c77c5-111">To add a control using the designer</span></span>  
  
1.  <span data-ttu-id="c77c5-112">Cliquez sur la page de l’onglet approprié afin qu’il apparaisse en premier.</span><span class="sxs-lookup"><span data-stu-id="c77c5-112">Click the appropriate tab page so that it appears on top.</span></span>  
  
2.  <span data-ttu-id="c77c5-113">Dessinez le contrôle sur la page d’onglets.</span><span class="sxs-lookup"><span data-stu-id="c77c5-113">Draw the control on the tab page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c77c5-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c77c5-114">See Also</span></span>  
 [<span data-ttu-id="c77c5-115">TabControl, contrôle</span><span class="sxs-lookup"><span data-stu-id="c77c5-115">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="c77c5-116">Vue d’ensemble du contrôle TabControl</span><span class="sxs-lookup"><span data-stu-id="c77c5-116">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="c77c5-117">Guide pratique pour modifier l'apparence du contrôle TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c77c5-117">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)  
 [<span data-ttu-id="c77c5-118">Guide pratique pour désactiver les pages d'onglets</span><span class="sxs-lookup"><span data-stu-id="c77c5-118">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="c77c5-119">Guide pratique pour ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c77c5-119">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
