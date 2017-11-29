---
title: "Comment : imprimer un formulaire à défilement variable (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- entire form [Visual Basic], printing
- scrollable form [Visual Basic], printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 380e0f833dc69718142809c99ed7615256dd2e73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a><span data-ttu-id="1b427-102">Comment : imprimer un formulaire à défilement variable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b427-102">How to: Print a Scrollable Form (Visual Basic)</span></span>
<span data-ttu-id="1b427-103">Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> vous permet d’imprimer rapidement une image d’un formulaire sans utiliser un composant <xref:System.Drawing.Printing.PrintDocument> .</span><span class="sxs-lookup"><span data-stu-id="1b427-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="1b427-104">Par défaut, seule la partie actuellement visible du formulaire est imprimée ; si un utilisateur a redimensionné le formulaire au moment de l’exécution, l’image ne peut pas être imprimée comme prévu.</span><span class="sxs-lookup"><span data-stu-id="1b427-104">By default, only the currently visible part of the form is printed; if a user has resized the form at run time, the image may not print as intended.</span></span> <span data-ttu-id="1b427-105">La procédure suivante montre comment imprimer la zone cliente complète d’un formulaire avec défilement, même si le formulaire a été redimensionné.</span><span class="sxs-lookup"><span data-stu-id="1b427-105">The following procedure shows how to print the complete client area of a scrollable form, even if the form has been resized.</span></span>  
  
 <span data-ttu-id="1b427-106">Les contrôles PowerPack ne sont plus inclus dans Visual Studio, mais vous pouvez les télécharger à partir du [Centre de téléchargement](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="1b427-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a><span data-ttu-id="1b427-107">Pour imprimer la zone cliente complète d’un formulaire avec défilement</span><span class="sxs-lookup"><span data-stu-id="1b427-107">To print the complete client area of a scrollable form</span></span>  
  
1.  <span data-ttu-id="1b427-108">Dans la **Boîte à outils**, cliquez sur l’onglet **Visual Basic PowerPacks** , puis faites glisser le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> sur le formulaire.</span><span class="sxs-lookup"><span data-stu-id="1b427-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="1b427-109">Le composant <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> va être ajouté à la barre d’état des composants.</span><span class="sxs-lookup"><span data-stu-id="1b427-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component will be added to the component tray.</span></span>  
  
2.  <span data-ttu-id="1b427-110">Dans la fenêtre **Propriétés** , définissez la propriété <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> sur <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="1b427-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="1b427-111">Ajoutez le code suivant dans le Gestionnaire d’événements approprié (par exemple, dans le `Click` Gestionnaire d’événements pour un **impression**`Button`).</span><span class="sxs-lookup"><span data-stu-id="1b427-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1b427-112">Sur certains systèmes d’exploitation, le texte ou les graphiques dessinés par des méthodes <xref:System.Drawing.Graphics> peuvent ne pas s’imprimer correctement.</span><span class="sxs-lookup"><span data-stu-id="1b427-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="1b427-113">Dans ce cas, vous ne pourrez pas imprimer avec le paramètre `Scrollable` .</span><span class="sxs-lookup"><span data-stu-id="1b427-113">In this case, you will not be able to print with the `Scrollable` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b427-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1b427-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="1b427-115">PrintForm, composant</span><span class="sxs-lookup"><span data-stu-id="1b427-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="1b427-116">Guide pratique : imprimer la zone cliente d’un formulaire</span><span class="sxs-lookup"><span data-stu-id="1b427-116">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [<span data-ttu-id="1b427-117">Guide pratique : imprimer des zones clientes et non clientes d’un formulaire</span><span class="sxs-lookup"><span data-stu-id="1b427-117">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
