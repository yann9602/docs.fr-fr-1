---
title: "Un formulaire de démarrage n’a pas été spécifié. | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_NoStartupForm
dev_langs:
- VB
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 37484a00a631577e80853822fff92b069dbad7f2
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="26861-102">Un formulaire de démarrage n'a pas été spécifié</span><span class="sxs-lookup"><span data-stu-id="26861-102">A startup form has not been specified</span></span>
<span data-ttu-id="26861-103">L’application utilise le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>de classe, mais ne spécifie pas le formulaire de démarrage.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></span><span class="sxs-lookup"><span data-stu-id="26861-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="26861-104">Cela peut se produire si le **activer l’infrastructure d’application** case à cocher est activée dans le Concepteur de projets, mais les **formulaire de démarrage** n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="26861-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="26861-105">Pour plus d’informations, consultez [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="26861-105">For more information, see [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="26861-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="26861-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="26861-107">Spécifiez un objet de démarrage de l’application.</span><span class="sxs-lookup"><span data-stu-id="26861-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="26861-108">Pour plus d’informations, consultez [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="26861-108">For more information, see [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2.  <span data-ttu-id="26861-109">Remplacer la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>pour définir le <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>propriété à l’écran de démarrage.</xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> </xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A></span><span class="sxs-lookup"><span data-stu-id="26861-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26861-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26861-110">See Also</span></span>  
 <span data-ttu-id="26861-111"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></span><span class="sxs-lookup"><span data-stu-id="26861-111"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase></span></span>   
 <span data-ttu-id="26861-112"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A></span><span class="sxs-lookup"><span data-stu-id="26861-112"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A></span></span>   
 <span data-ttu-id="26861-113"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A></xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A></span><span class="sxs-lookup"><span data-stu-id="26861-113"><xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A></span></span>   
<span data-ttu-id="26861-114"> [Vue d’ensemble du modèle d’application Visual Basic](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)</span><span class="sxs-lookup"><span data-stu-id="26861-114"> [Overview of the Visual Basic Application Model](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)</span></span>
