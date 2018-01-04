---
title: "Comment : afficher l'aide contextuelle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d139c283d002ac76005f22385d83190144c5082
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-pop-up-help"></a><span data-ttu-id="fddcc-102">Comment : afficher l'aide contextuelle</span><span class="sxs-lookup"><span data-stu-id="fddcc-102">How to: Display Pop-up Help</span></span>
<span data-ttu-id="fddcc-103">Permet d’afficher l’aide dans les Windows Forms s’effectue via le **aide** bouton situé sur le côté droit de la barre de titre, accessible via la <xref:System.Windows.Forms.Form.HelpButton%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="fddcc-103">One way to display Help on Windows Forms is through the **Help** button, located on the right side of the title bar, accessible through the <xref:System.Windows.Forms.Form.HelpButton%2A> property.</span></span> <span data-ttu-id="fddcc-104">Ce type d’affichage de l’aide convient parfaitement aux boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="fddcc-104">This type of Help display is well-suited for use with dialog boxes.</span></span> <span data-ttu-id="fddcc-105">Les boîtes de dialogue modales (affichées avec la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A>) ont des difficultés à afficher les systèmes d'aide externes, car elles doivent être fermées pour que le focus puisse basculer vers une autre fenêtre.</span><span class="sxs-lookup"><span data-stu-id="fddcc-105">Dialog boxes shown modally (with the <xref:System.Windows.Forms.Form.ShowDialog%2A> method) have trouble bringing up external Help systems, because modal dialog boxes need to be closed before focus can shift to another window.</span></span> <span data-ttu-id="fddcc-106">En outre, à l’aide de la **aide** bouton nécessite qu’il y a aucune **réduire** bouton ou **agrandir** affiché dans la barre de titre.</span><span class="sxs-lookup"><span data-stu-id="fddcc-106">Additionally, using the **Help** button requires that there is no **Minimize** button or **Maximize** button shown in the title bar.</span></span> <span data-ttu-id="fddcc-107">Il s’agit une convention de la boîte de dialogue standard, tandis que les formulaires possèdent généralement **réduire** et **agrandir** boutons.</span><span class="sxs-lookup"><span data-stu-id="fddcc-107">This is a standard dialog-box convention, whereas forms usually have **Minimize** and **Maximize** buttons.</span></span>  
  
 <span data-ttu-id="fddcc-108">Sachez que vous pouvez également utiliser le composant <xref:System.Windows.Forms.HelpProvider> pour lier des contrôles à des fichiers d'un système d'aide, même si vous avez implémenté l'aide contextuelle.</span><span class="sxs-lookup"><span data-stu-id="fddcc-108">Be aware that you can also use the <xref:System.Windows.Forms.HelpProvider> component to link controls to files in a Help system, even if you have implemented pop-up Help.</span></span> <span data-ttu-id="fddcc-109">Pour plus d’informations, consultez [fourniture d’aide dans une Application Windows](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).</span><span class="sxs-lookup"><span data-stu-id="fddcc-109">For more information, see [Providing Help in a Windows Application](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fddcc-110">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="fddcc-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="fddcc-111">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="fddcc-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="fddcc-112">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="fddcc-112">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-display-pop-up-help"></a><span data-ttu-id="fddcc-113">Pour afficher une aide contextuelle</span><span class="sxs-lookup"><span data-stu-id="fddcc-113">To display pop-up Help</span></span>  
  
1.  <span data-ttu-id="fddcc-114">Faites glisser un [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) composant à partir de la boîte à outils vers votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="fddcc-114">Drag a [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) component from the Toolbox to your form.</span></span>  
  
     <span data-ttu-id="fddcc-115">Il sera placé dans la barre d'état en bas du Concepteur Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fddcc-115">It will sit in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="fddcc-116">Dans la fenêtre Propriétés, affectez la valeur `true` à la propriété <xref:System.Windows.Forms.Form.HelpButton%2A>.</span><span class="sxs-lookup"><span data-stu-id="fddcc-116">In the Properties window, set the <xref:System.Windows.Forms.Form.HelpButton%2A> property to `true`.</span></span> <span data-ttu-id="fddcc-117">Ceci affichera un bouton avec un point d'interrogation sur le côté droit de la barre de titre du formulaire.</span><span class="sxs-lookup"><span data-stu-id="fddcc-117">This will display a button with a question mark in it on the right side of the title bar of the form.</span></span>  
  
3.  <span data-ttu-id="fddcc-118">Pour que le <xref:System.Windows.Forms.Form.HelpButton%2A> soit affiché, il faut que les propriétés <xref:System.Windows.Forms.Form.MinimizeBox%2A> et <xref:System.Windows.Forms.Form.MaximizeBox%2A>  du formulaire aient la valeur `false`, que la propriété <xref:System.Windows.Forms.Form.ControlBox%2A> ait la valeur `true` et que la propriété <xref:System.Windows.Forms.Form.FormBorderStyle%2A> ait l'une des valeurs suivantes : <xref:System.Windows.Forms.FormBorderStyle.FixedSingle>, <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> ou <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span><span class="sxs-lookup"><span data-stu-id="fddcc-118">In order for the <xref:System.Windows.Forms.Form.HelpButton%2A> to display, the form's <xref:System.Windows.Forms.Form.MinimizeBox%2A> and <xref:System.Windows.Forms.Form.MaximizeBox%2A> properties must be set to `false`, the <xref:System.Windows.Forms.Form.ControlBox%2A> property set to `true`, and the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to one of the following values: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle>, <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> or <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span></span>  
  
4.  <span data-ttu-id="fddcc-119">Sélectionnez le contrôle pour lequel vous souhaitez afficher l'aide sur votre formulaire et définissez la chaîne d'aide dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="fddcc-119">Select the control for which you want to show help on your form and set the Help string in the Properties window.</span></span> <span data-ttu-id="fddcc-120">C’est la chaîne de texte qui s’affichera dans une fenêtre similaire à un [info-bulle](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="fddcc-120">This is the string of text that will be displayed in a window similar to a [ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).</span></span>  
  
5.  <span data-ttu-id="fddcc-121">Appuyez sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="fddcc-121">Press **F5**.</span></span>  
  
6.  <span data-ttu-id="fddcc-122">Appuyez sur la **aide** sur la barre de titre, puis cliquez sur le contrôle sur lequel vous définissez la chaîne d’aide.</span><span class="sxs-lookup"><span data-stu-id="fddcc-122">Press the **Help** button on the title bar and click the control on which you set the Help string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fddcc-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fddcc-123">See Also</span></span>  
 [<span data-ttu-id="fddcc-124">Affichage sous forme d’info-bulles de l’aide relative aux contrôles</span><span class="sxs-lookup"><span data-stu-id="fddcc-124">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [<span data-ttu-id="fddcc-125">Intégration de l’aide d’utilisateur dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fddcc-125">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="fddcc-126">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fddcc-126">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
