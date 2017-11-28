---
title: "Comment : enregistrer des messages lorsque l'application démarre ou s'arrête (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16235e245fd71f16edb67003cf237bcee3a6855e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a><span data-ttu-id="41574-102">Comment : enregistrer des messages lorsque l'application démarre ou s'arrête (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41574-102">How to: Log Messages When the Application Starts or Shuts Down (Visual Basic)</span></span>
<span data-ttu-id="41574-103">Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les événements qui se produisent dans votre application.</span><span class="sxs-lookup"><span data-stu-id="41574-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="41574-104">Cet exemple montre comment utiliser la méthode `My.Application.Log.WriteEntry` avec les événements `Startup` et `Shutdown` pour enregistrer des informations de traçage.</span><span class="sxs-lookup"><span data-stu-id="41574-104">This example shows how to use the `My.Application.Log.WriteEntry` method with the `Startup` and `Shutdown` events to write tracing information.</span></span>  
  
### <a name="to-access-the-applications-event-handler-code"></a><span data-ttu-id="41574-105">Pour accéder au code du gestionnaire d’événements de l’application</span><span class="sxs-lookup"><span data-stu-id="41574-105">To access the application's event-handler code</span></span>  
  
1.  <span data-ttu-id="41574-106">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="41574-106">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="41574-107">Dans le menu **Projet** , choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="41574-107">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="41574-108">Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="41574-108">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="41574-109">Cliquez sur le bouton **Afficher les événements de l’application** pour ouvrir l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="41574-109">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="41574-110">Le fichier ApplicationEvents.vb s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="41574-110">This opens the ApplicationEvents.vb file.</span></span>  
  
### <a name="to-log-messages-when-the-application-starts"></a><span data-ttu-id="41574-111">Pour enregistrer des messages quand l’application démarre</span><span class="sxs-lookup"><span data-stu-id="41574-111">To log messages when the application starts</span></span>  
  
1.  <span data-ttu-id="41574-112">Ouvrez le fichier ApplicationEvents.vb dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="41574-112">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="41574-113">Dans le menu **Général** , choisissez **Événements MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="41574-113">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="41574-114">Dans le menu **Déclarations** , choisissez **Démarrage**.</span><span class="sxs-lookup"><span data-stu-id="41574-114">On the **Declarations** menu, choose **Startup**.</span></span>  
  
     <span data-ttu-id="41574-115">L’application déclenche l’événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> avant l’exécution de l’application principale.</span><span class="sxs-lookup"><span data-stu-id="41574-115">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> event before the main application runs.</span></span>  
  
3.  <span data-ttu-id="41574-116">Ajoutez la méthode `My.Application.Log.WriteEntry` au gestionnaire d’événements `Startup` .</span><span class="sxs-lookup"><span data-stu-id="41574-116">Add the `My.Application.Log.WriteEntry` method to the `Startup` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a><span data-ttu-id="41574-117">Pour enregistrer des messages quand l’application s’arrête</span><span class="sxs-lookup"><span data-stu-id="41574-117">To log messages when the application shuts down</span></span>  
  
1.  <span data-ttu-id="41574-118">Ouvrez le fichier ApplicationEvents.vb dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="41574-118">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="41574-119">Dans le menu **Général** , choisissez **Événements MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="41574-119">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
2.  <span data-ttu-id="41574-120">Dans le menu **Déclarations** , choisissez **Arrêt**.</span><span class="sxs-lookup"><span data-stu-id="41574-120">On the **Declarations** menu, choose **Shutdown**.</span></span>  
  
     <span data-ttu-id="41574-121">L’application déclenche l’événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> après l’exécution de l’application principale, mais avant qu’elle s’arrête.</span><span class="sxs-lookup"><span data-stu-id="41574-121">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> event after the main application runs, but before it shuts down.</span></span>  
  
3.  <span data-ttu-id="41574-122">Ajoutez la méthode `My.Application.Log.WriteEntry` au gestionnaire d’événements `Shutdown` .</span><span class="sxs-lookup"><span data-stu-id="41574-122">Add the `My.Application.Log.WriteEntry` method to the `Shutdown` event handler.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="41574-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="41574-123">Example</span></span>  
 <span data-ttu-id="41574-124">Vous pouvez utiliser le **Concepteur de projets** pour accéder aux événements de l’application dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="41574-124">You can use the **Project Designer** to access the application events in the Code Editor.</span></span> <span data-ttu-id="41574-125">Pour plus d’informations, consultez [Page Application, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="41574-125">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="41574-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41574-126">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="41574-127">Page Application, Concepteur de projets (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="41574-127">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="41574-128">Utilisation des journaux des applications</span><span class="sxs-lookup"><span data-stu-id="41574-128">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
