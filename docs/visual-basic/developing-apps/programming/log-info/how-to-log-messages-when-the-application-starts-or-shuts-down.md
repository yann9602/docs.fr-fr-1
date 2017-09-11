---
title: "Comment : enregistrer des messages lorsque l'application démarre ou s'arrête (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event
- event logs, startup
- Shutdown event
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fa5bf57ac5245e9363089b85607b7e6d1a00ba14
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="50ee1-102">Comment : enregistrer des messages lorsque l'application démarre ou s'arrête (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50ee1-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="50ee1-103">Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les événements qui se produisent dans votre application.</span><span class="sxs-lookup"><span data-stu-id="50ee1-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="50ee1-104">Cet exemple montre comment utiliser la méthode `My.Application.Log.WriteEntry` avec les événements `Startup` et `Shutdown` pour enregistrer des informations de traçage.</span><span class="sxs-lookup"><span data-stu-id="50ee1-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="50ee1-105">Pour accéder au code du gestionnaire d’événements de l’application</span><span class="sxs-lookup"><span data-stu-id="50ee1-105">To access the application's event-handler code</span></span>  
  
1.  <span data-ttu-id="50ee1-106">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="50ee1-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="50ee1-107">Dans le menu **Projet** , choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="50ee1-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="50ee1-108">Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="50ee1-108">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="50ee1-109">Cliquez sur le bouton **Afficher les événements de l’application** pour ouvrir l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="50ee1-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="50ee1-110">Le fichier ApplicationEvents.vb s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="50ee1-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="50ee1-111">Pour enregistrer des messages quand l’application démarre</span><span class="sxs-lookup"><span data-stu-id="50ee1-111">To log messages when the application starts</span></span>  
  
1.  <span data-ttu-id="50ee1-112">Ouvrez le fichier ApplicationEvents.vb dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="50ee1-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="50ee1-113">Dans le menu **Général** , choisissez **Événements MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="50ee1-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="50ee1-114">Dans le menu **Déclarations** , choisissez **Démarrage**.</span><span class="sxs-lookup"><span data-stu-id="50ee1-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="50ee1-115">L’application déclenche l’événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> avant l’exécution de l’application principale.</span><span class="sxs-lookup"><span data-stu-id="50ee1-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3.  <span data-ttu-id="50ee1-116">Ajoutez la méthode `My.Application.Log.WriteEntry` au gestionnaire d’événements `Startup` .</span><span class="sxs-lookup"><span data-stu-id="50ee1-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     <span data-ttu-id="50ee1-117">[!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="50ee1-117">[!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]</span></span>  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="50ee1-118">Pour enregistrer des messages quand l’application s’arrête</span><span class="sxs-lookup"><span data-stu-id="50ee1-118">To log messages when the application shuts down</span></span>  
  
1.  <span data-ttu-id="50ee1-119">Ouvrez le fichier ApplicationEvents.vb dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="50ee1-119">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="50ee1-120">Dans le menu **Général** , choisissez **Événements MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="50ee1-120">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="50ee1-121">Dans le menu **Déclarations** , choisissez **Arrêt**.</span><span class="sxs-lookup"><span data-stu-id="50ee1-121">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="50ee1-122">L’application déclenche l’événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> après l’exécution de l’application principale, mais avant qu’elle s’arrête.</span><span class="sxs-lookup"><span data-stu-id="50ee1-122">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3.  <span data-ttu-id="50ee1-123">Ajoutez la méthode `My.Application.Log.WriteEntry` au gestionnaire d’événements `Shutdown` .</span><span class="sxs-lookup"><span data-stu-id="50ee1-123">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     <span data-ttu-id="50ee1-124">[!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="50ee1-124">[!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="50ee1-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="50ee1-125">Example</span></span>  
 <span data-ttu-id="50ee1-126">Vous pouvez utiliser le **Concepteur de projets** pour accéder aux événements de l’application dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="50ee1-126">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="50ee1-127">Pour plus d’informations, consultez [Page Application, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="50ee1-127">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="50ee1-128">[!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="50ee1-128">[!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50ee1-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50ee1-129">See Also</span></span>  
 <span data-ttu-id="50ee1-130"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="50ee1-130"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="50ee1-131"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="50ee1-131"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>   
 <span data-ttu-id="50ee1-132"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span><span class="sxs-lookup"><span data-stu-id="50ee1-132"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span></span>   
 <span data-ttu-id="50ee1-133">[Page Application, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="50ee1-133">[Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span></span>  
 [<span data-ttu-id="50ee1-134">Utilisation des journaux des applications</span><span class="sxs-lookup"><span data-stu-id="50ee1-134">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)

