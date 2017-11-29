---
title: "Comment : ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabPage control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 480633db-413a-45d2-9c8f-0427cc13adbe
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 02bcf434baee0c27ca2674817df0e4033effb125
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol-using-the-designer"></a><span data-ttu-id="0ea26-102">Comment : ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="0ea26-102">How to: Add and Remove Tabs with the Windows Forms TabControl Using the Designer</span></span>
<span data-ttu-id="0ea26-103">Lorsque vous placez un <xref:System.Windows.Forms.TabControl> contrôle sur votre formulaire, il contient deux onglets par défaut.</span><span class="sxs-lookup"><span data-stu-id="0ea26-103">When you place a <xref:System.Windows.Forms.TabControl> control on your form, it contains two tabs by default.</span></span> <span data-ttu-id="0ea26-104">Vous pouvez ajouter ou supprimer des onglets à l’aide du concepteur.</span><span class="sxs-lookup"><span data-stu-id="0ea26-104">You can add or remove tabs using the designer.</span></span>  
  
 <span data-ttu-id="0ea26-105">La procédure suivante requiert un **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.TabControl> contrôle.</span><span class="sxs-lookup"><span data-stu-id="0ea26-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TabControl> control.</span></span> <span data-ttu-id="0ea26-106">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0ea26-106">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ea26-107">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="0ea26-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0ea26-108">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="0ea26-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0ea26-109">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="0ea26-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-a-tab-using-the-designer"></a><span data-ttu-id="0ea26-110">Pour ajouter ou supprimer un onglet à l’aide du Concepteur</span><span class="sxs-lookup"><span data-stu-id="0ea26-110">To add or remove a tab using the designer</span></span>  
  
-   <span data-ttu-id="0ea26-111">Dans la balise du contrôle, cliquez sur **ajouter un onglet** ou **onglet supprimer**</span><span class="sxs-lookup"><span data-stu-id="0ea26-111">On the control's smart tag, click **Add Tab** or **Remove Tab**</span></span>  
  
     <span data-ttu-id="0ea26-112">ou</span><span class="sxs-lookup"><span data-stu-id="0ea26-112">-or-</span></span>  
  
     <span data-ttu-id="0ea26-113">Dans le **propriétés** fenêtre, cliquez sur le **points de suspension** bouton (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) à côté le <xref:System.Windows.Forms.TabControl.TabPages%2A> propriété pour ouvrir la **éditeur de collections TabPage**.</span><span class="sxs-lookup"><span data-stu-id="0ea26-113">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.TabControl.TabPages%2A> property to open the **TabPage Collection Editor**.</span></span> <span data-ttu-id="0ea26-114">Cliquez sur le **ajouter** ou **supprimer** bouton.</span><span class="sxs-lookup"><span data-stu-id="0ea26-114">Click the **Add** or **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea26-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ea26-115">See Also</span></span>  
 [<span data-ttu-id="0ea26-116">TabControl, contrôle</span><span class="sxs-lookup"><span data-stu-id="0ea26-116">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="0ea26-117">Vue d’ensemble du contrôle TabControl</span><span class="sxs-lookup"><span data-stu-id="0ea26-117">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="0ea26-118">Guide pratique pour ajouter un contrôle à une page d'onglet</span><span class="sxs-lookup"><span data-stu-id="0ea26-118">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="0ea26-119">Guide pratique pour désactiver les pages d'onglets</span><span class="sxs-lookup"><span data-stu-id="0ea26-119">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="0ea26-120">Guide pratique pour modifier l'apparence du contrôle TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0ea26-120">How to: Change the Appearance of the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
