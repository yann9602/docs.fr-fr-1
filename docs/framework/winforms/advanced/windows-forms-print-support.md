---
title: Prise en charge de l'impression dans les Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 81f89ee41eb9f8b492ab12e30ae4580cdffbd8f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-print-support"></a><span data-ttu-id="08115-102">Prise en charge de l'impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08115-102">Windows Forms Print Support</span></span>
<span data-ttu-id="08115-103">L’impression dans les Windows Forms consiste principalement à l’aide de la [composant PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) composant pour permettre à l’utilisateur d’imprimer et le [contrôle PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) contrôle, [PrintDialog Composant](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) et [composant PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) composants afin de fournir une interface graphique familière aux utilisateurs habitués au système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="08115-103">Printing in Windows Forms consists primarily of using the [PrintDocument Component](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) component to enable the user to print, and the [PrintPreviewDialog Control](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) control, [PrintDialog Component](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) and [PageSetupDialog Component](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) components to provide a familiar graphical interface to users accustomed to the Windows operating system.</span></span>  
  
 <span data-ttu-id="08115-104">En général, vous créez une nouvelle instance de la <xref:System.Drawing.Printing.PrintDocument> composant, définir les propriétés qui décrivent les éléments à imprimer à l’aide de la <xref:System.Drawing.Printing.PrinterSettings> et <xref:System.Drawing.Printing.PageSettings> classes, puis appelez le <xref:System.Drawing.Printing.PrintDocument.Print%2A> méthode pour imprimer le document.</span><span class="sxs-lookup"><span data-stu-id="08115-104">Typically, you create a new instance of the <xref:System.Drawing.Printing.PrintDocument> component, set the properties that describe what to print using the <xref:System.Drawing.Printing.PrinterSettings> and <xref:System.Drawing.Printing.PageSettings> classes, and call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to actually print the document.</span></span>  
  
 <span data-ttu-id="08115-105">Au cours de l’impression à partir d’une application Windows, le <xref:System.Drawing.Printing.PrintDocument> composant affiche une boîte de dialogue d’impression d’annulation afin d’alerter les utilisateurs de l’impression en cours et pour autoriser le travail d’impression doit être annulée.</span><span class="sxs-lookup"><span data-stu-id="08115-105">During the course of printing from a Windows-based application, the <xref:System.Drawing.Printing.PrintDocument> component will show an abort print dialog box to alert users to the fact that printing is occurring and to allow the print job to be canceled.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08115-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="08115-106">In This Section</span></span>  
 [<span data-ttu-id="08115-107">Guide pratique pour créer des travaux d’impression Windows Forms standard</span><span class="sxs-lookup"><span data-stu-id="08115-107">How to: Create Standard Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 <span data-ttu-id="08115-108">Explique comment utiliser le <xref:System.Drawing.Printing.PrintDocument> composant pour imprimer à partir d’un Windows Form.</span><span class="sxs-lookup"><span data-stu-id="08115-108">Explains how to use the <xref:System.Drawing.Printing.PrintDocument> component to print from a Windows Form.</span></span>  
  
 [<span data-ttu-id="08115-109">Guide pratique pour capturer une entrée d’utilisateur à partir d’un composant PrintDialog au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="08115-109">How to: Capture User Input from a PrintDialog at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 <span data-ttu-id="08115-110">Explique comment modifier les options d’impression sélectionnées par programme en utilisant le <xref:System.Windows.Forms.PrintDialog> composant.</span><span class="sxs-lookup"><span data-stu-id="08115-110">Explains how to modify selected print options programmatically using the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="08115-111">Guide pratique pour choisir les imprimantes connectées à l'ordinateur d'un utilisateur dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08115-111">How to: Choose the Printers Attached to a User's Computer in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 <span data-ttu-id="08115-112">Décrit la modification de l’imprimante à utiliser à l’aide de la <xref:System.Windows.Forms.PrintDialog> composant au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="08115-112">Describes changing the printer to print to using the <xref:System.Windows.Forms.PrintDialog> component at run time.</span></span>  
  
 [<span data-ttu-id="08115-113">Comment : imprimer des graphiques dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08115-113">How to: Print Graphics in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 <span data-ttu-id="08115-114">Décrit l’envoi de graphismes à l’imprimante.</span><span class="sxs-lookup"><span data-stu-id="08115-114">Describes sending graphics to the printer.</span></span>  
  
 [<span data-ttu-id="08115-115">Comment : imprimer un fichier texte composé de plusieurs pages dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08115-115">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 <span data-ttu-id="08115-116">Décrit l’envoi de texte à l’imprimante.</span><span class="sxs-lookup"><span data-stu-id="08115-116">Describes sending text to the printer.</span></span>  
  
 [<span data-ttu-id="08115-117">Guide pratique pour terminer des travaux d'impression Windows Forms</span><span class="sxs-lookup"><span data-stu-id="08115-117">How to: Complete Windows Forms Print Jobs</span></span>](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 <span data-ttu-id="08115-118">Explique comment avertir les utilisateurs de l’achèvement d’un travail d’impression.</span><span class="sxs-lookup"><span data-stu-id="08115-118">Explains how to alert users to the completion of a print job.</span></span>  
  
 [<span data-ttu-id="08115-119">Guide pratique pour imprimer un Windows Form</span><span class="sxs-lookup"><span data-stu-id="08115-119">How to: Print a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 <span data-ttu-id="08115-120">Montre comment imprimer une copie de l’écran actuel.</span><span class="sxs-lookup"><span data-stu-id="08115-120">Shows how to print a copy of the current form.</span></span>  
  
 [<span data-ttu-id="08115-121">Guide pratique pour imprimer dans les Windows Forms en utilisant l'aperçu avant impression</span><span class="sxs-lookup"><span data-stu-id="08115-121">How to: Print in Windows Forms Using Print Preview</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 <span data-ttu-id="08115-122">Montre comment utiliser un <xref:System.Windows.Forms.PrintPreviewDialog> pour imprimer un document.</span><span class="sxs-lookup"><span data-stu-id="08115-122">Shows how to use a <xref:System.Windows.Forms.PrintPreviewDialog> for printing a document.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="08115-123">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="08115-123">Related Sections</span></span>  
 [<span data-ttu-id="08115-124">Composant PrintDocument</span><span class="sxs-lookup"><span data-stu-id="08115-124">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 <span data-ttu-id="08115-125">Explique comment utiliser le <xref:System.Drawing.Printing.PrintDocument> composant.</span><span class="sxs-lookup"><span data-stu-id="08115-125">Explains usage of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
 [<span data-ttu-id="08115-126">PrintDialog, composant</span><span class="sxs-lookup"><span data-stu-id="08115-126">PrintDialog Component</span></span>](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 <span data-ttu-id="08115-127">Explique comment utiliser le <xref:System.Windows.Forms.PrintDialog> composant.</span><span class="sxs-lookup"><span data-stu-id="08115-127">Explains usage of the <xref:System.Windows.Forms.PrintDialog> component.</span></span>  
  
 [<span data-ttu-id="08115-128">PrintPreviewDialog, contrôle</span><span class="sxs-lookup"><span data-stu-id="08115-128">PrintPreviewDialog Control</span></span>](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 <span data-ttu-id="08115-129">Explique comment utiliser le <xref:System.Windows.Forms.PrintPreviewDialog> contrôle.</span><span class="sxs-lookup"><span data-stu-id="08115-129">Explains usage of the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span>  
  
 [<span data-ttu-id="08115-130">PageSetupDialog, composant</span><span class="sxs-lookup"><span data-stu-id="08115-130">PageSetupDialog Component</span></span>](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 <span data-ttu-id="08115-131">Explique comment utiliser le <xref:System.Windows.Forms.PageSetupDialog> composant.</span><span class="sxs-lookup"><span data-stu-id="08115-131">Explains usage of the <xref:System.Windows.Forms.PageSetupDialog> component.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="08115-132">Décrit les classes dans le <xref:System.Drawing.Printing> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="08115-132">Describes the classes in the <xref:System.Drawing.Printing> namespace.</span></span>
