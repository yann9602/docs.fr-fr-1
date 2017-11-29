---
title: 'Comment : imprimer la zone cliente d''un formulaire (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef42dd3c809ff0a1594350e252d4c4aa2f0ec004
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a><span data-ttu-id="2d14a-102">Comment : imprimer la zone cliente d'un formulaire (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d14a-102">How to: Print the Client Area of a Form (Visual Basic)</span></span>
<span data-ttu-id="2d14a-103">Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> vous permet d’imprimer rapidement une image d’un formulaire sans utiliser un composant <xref:System.Drawing.Printing.PrintDocument> .</span><span class="sxs-lookup"><span data-stu-id="2d14a-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="2d14a-104">La procédure suivante montre comment imprimer uniquement la zone cliente d’un formulaire, sans la barre de titre, les bordures et les barres de défilement.</span><span class="sxs-lookup"><span data-stu-id="2d14a-104">The following procedure shows how to print just the client area of a form, without the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="2d14a-105">Les contrôles PowerPack ne sont plus inclus dans Visual Studio, mais vous pouvez les télécharger à partir du [Centre de téléchargement](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="2d14a-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-client-area-of-a-form"></a><span data-ttu-id="2d14a-106">Pour imprimer la zone cliente d’un formulaire</span><span class="sxs-lookup"><span data-stu-id="2d14a-106">To print the client area of a form</span></span>  
  
1.  <span data-ttu-id="2d14a-107">Dans la **Boîte à outils**, cliquez sur l’onglet **Visual Basic PowerPacks** , puis faites glisser le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="2d14a-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="2d14a-108">Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> est ajouté à la barre d’état des composants.</span><span class="sxs-lookup"><span data-stu-id="2d14a-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="2d14a-109">Dans la fenêtre **Propriétés** , définissez la propriété <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> sur <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="2d14a-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="2d14a-110">Ajoutez le code suivant dans le Gestionnaire d’événements approprié (par exemple, dans le `Click` Gestionnaire d’événements pour un **impression**`Button`).</span><span class="sxs-lookup"><span data-stu-id="2d14a-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="2d14a-111">Sur certains systèmes d’exploitation, le texte ou les graphiques dessinés par des méthodes <xref:System.Drawing.Graphics> peuvent ne pas s’imprimer correctement.</span><span class="sxs-lookup"><span data-stu-id="2d14a-111">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="2d14a-112">Dans ce cas, utilisez la méthode d’impression compatible : `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span><span class="sxs-lookup"><span data-stu-id="2d14a-112">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d14a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d14a-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="2d14a-114">PrintForm, composant</span><span class="sxs-lookup"><span data-stu-id="2d14a-114">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="2d14a-115">Guide pratique : imprimer des zones clientes et non clientes d’un formulaire</span><span class="sxs-lookup"><span data-stu-id="2d14a-115">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [<span data-ttu-id="2d14a-116">Guide pratique : imprimer un formulaire à défilement variable</span><span class="sxs-lookup"><span data-stu-id="2d14a-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
