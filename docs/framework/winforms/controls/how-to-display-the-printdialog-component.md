---
title: Guide pratique pour afficher le composant PrintDialog
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7e1162a4e926d5be35f8f7bb7cdeb92264f293aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-the-printdialog-component"></a><span data-ttu-id="650d0-102">Guide pratique pour afficher le composant PrintDialog</span><span class="sxs-lookup"><span data-stu-id="650d0-102">How to: Display the PrintDialog Component</span></span>
<span data-ttu-id="650d0-103">Le <xref:System.Windows.Forms.PrintDialog> composant est la boîte de dialogue d’impression Windows standard que la plupart de vos utilisateurs seront familiers.</span><span class="sxs-lookup"><span data-stu-id="650d0-103">The <xref:System.Windows.Forms.PrintDialog> component is the standard Windows print dialog box that many of your users will be familiar with.</span></span> <span data-ttu-id="650d0-104">Étant donné que vos utilisateurs seront immédiatement à l’aise avec elle, il serait utile pour pouvoir utiliser le <xref:System.Windows.Forms.PrintDialog> composant.</span><span class="sxs-lookup"><span data-stu-id="650d0-104">Because your users will be immediately comfortable with it, it would be beneficial for you to use the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
### <a name="to-display-the-printdialog-component"></a><span data-ttu-id="650d0-105">Pour afficher le composant PrintDialog</span><span class="sxs-lookup"><span data-stu-id="650d0-105">To display the PrintDialog component</span></span>  
  
-   <span data-ttu-id="650d0-106">Appelez le <xref:System.Windows.Forms.Form.ShowDialog%2A> méthode à partir du code de votre application.</span><span class="sxs-lookup"><span data-stu-id="650d0-106">Call the <xref:System.Windows.Forms.Form.ShowDialog%2A> method from within the code of your application.</span></span>  
  
     <span data-ttu-id="650d0-107">Une fois le composant affiché, les utilisateurs interagissent avec lui et définissent les propriétés du travail d’impression.</span><span class="sxs-lookup"><span data-stu-id="650d0-107">Once the component is shown, users will interact with it, setting the properties of the print job.</span></span> <span data-ttu-id="650d0-108">Celles-ci sont enregistrées dans le <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` classe (et le <xref:System.Drawing.Printing.PageSettings> classe, si l’utilisateur accède à la [PageSetupDialog (composant)](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) via la <xref:System.Windows.Forms.PrintDialog> composant) associé à ce travail d’impression.</span><span class="sxs-lookup"><span data-stu-id="650d0-108">These are saved in the <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` class (and the <xref:System.Drawing.Printing.PageSettings> class, if the user accesses the [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) through the <xref:System.Windows.Forms.PrintDialog> component) associated with that print job.</span></span> <span data-ttu-id="650d0-109">Vous pouvez ensuite faire des appels aux propriétés qu’elles définissent pour déterminer les caractéristiques du travail d’impression.</span><span class="sxs-lookup"><span data-stu-id="650d0-109">You can then make calls to the properties they set to determine the specifics of the print job.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="650d0-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="650d0-110">See Also</span></span>  
 [<span data-ttu-id="650d0-111">Guide pratique pour créer des travaux d’impression Windows Forms standard</span><span class="sxs-lookup"><span data-stu-id="650d0-111">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [<span data-ttu-id="650d0-112">Guide pratique pour capturer une entrée d’utilisateur à partir d’un composant PrintDialog au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="650d0-112">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [<span data-ttu-id="650d0-113">PrintPreviewDialog, contrôle</span><span class="sxs-lookup"><span data-stu-id="650d0-113">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [<span data-ttu-id="650d0-114">PrintDialog, composant</span><span class="sxs-lookup"><span data-stu-id="650d0-114">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [<span data-ttu-id="650d0-115">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="650d0-115">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="650d0-116">Contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="650d0-116">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)
