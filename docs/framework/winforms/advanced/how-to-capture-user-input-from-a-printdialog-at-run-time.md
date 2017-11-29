---
title: "Comment : capturer une entrée d'utilisateur à partir d'un composant PrintDialog au moment de l'exécution"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6c942cb5f005177b74dd25a9725b4990553adbb8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a><span data-ttu-id="7036c-102">Comment : capturer une entrée d'utilisateur à partir d'un composant PrintDialog au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="7036c-102">How to: Capture User Input from a PrintDialog at Run Time</span></span>
<span data-ttu-id="7036c-103">Vous pouvez configurer les options relatives à l’impression au moment du design, vous devez parfois modifier ces options en cours d’exécution, probablement en raison des choix effectués par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7036c-103">While you can set options related to printing at design time, you will sometimes want to change these options at run time, most likely because of choices made by the user.</span></span> <span data-ttu-id="7036c-104">Vous pouvez capturer l’entrée d’utilisateur pour l’impression d’un document à l’aide de la <xref:System.Windows.Forms.PrintDialog> et <xref:System.Drawing.Printing.PrintDocument> composants.</span><span class="sxs-lookup"><span data-stu-id="7036c-104">You can capture user input for printing a document using the <xref:System.Windows.Forms.PrintDialog> and the <xref:System.Drawing.Printing.PrintDocument> components.</span></span>  
  
### <a name="to-change-print-options-programmatically"></a><span data-ttu-id="7036c-105">Pour modifier les options d’impression par programmation</span><span class="sxs-lookup"><span data-stu-id="7036c-105">To change print options programmatically</span></span>  
  
1.  <span data-ttu-id="7036c-106">Ajouter un <xref:System.Windows.Forms.PrintDialog> et une <xref:System.Drawing.Printing.PrintDocument> à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="7036c-106">Add a <xref:System.Windows.Forms.PrintDialog> and a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="7036c-107">Définir le <xref:System.Windows.Forms.PrintDialog.Document%2A> propriété de la <xref:System.Windows.Forms.PrintDialog> à la <xref:System.Drawing.Printing.PrintDocument> ajouté au formulaire.</span><span class="sxs-lookup"><span data-stu-id="7036c-107">Set the <xref:System.Windows.Forms.PrintDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintDialog> to the <xref:System.Drawing.Printing.PrintDocument> added to the form.</span></span>  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  <span data-ttu-id="7036c-108">Afficher le <xref:System.Windows.Forms.PrintDialog> composant à l’aide de la <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="7036c-108">Display the <xref:System.Windows.Forms.PrintDialog> component by using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span>  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  <span data-ttu-id="7036c-109">Choix de l’impression de l’utilisateur à partir de la boîte de dialogue seront copiés dans le <xref:System.Drawing.Printing.PrinterSettings> propriété de la <xref:System.Drawing.Printing.PrintDocument> composant.</span><span class="sxs-lookup"><span data-stu-id="7036c-109">The user's printing choices from the dialog will be copied to the <xref:System.Drawing.Printing.PrinterSettings> property of the <xref:System.Drawing.Printing.PrintDocument> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7036c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7036c-110">See Also</span></span>  
 [<span data-ttu-id="7036c-111">Comment : imprimer un fichier texte composé de plusieurs pages dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7036c-111">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [<span data-ttu-id="7036c-112">Prise en charge de l’impression dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7036c-112">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
