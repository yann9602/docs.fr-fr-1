---
title: Guide pratique pour enregistrer des exceptions en Visual Basic
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
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
caps.latest.revision: 19
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: adf2dc683a139d21f24379efc779d4510a2057eb
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-log-exceptions-in-visual-basic"></a><span data-ttu-id="5ec2d-102">Guide pratique pour enregistrer des exceptions en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ec2d-102">How to: Log Exceptions in Visual Basic</span></span>
<span data-ttu-id="5ec2d-103">Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les exceptions qui se produisent dans votre application.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-103">You can use the `My.Application.Log` and `My.Log` objects to log information about exceptions that occur in your application.</span></span> <span data-ttu-id="5ec2d-104">Ces exemples montrent comment utiliser la méthode `My.Application.Log.WriteException` pour enregistrer des exceptions que vous interceptez explicitement et des exceptions qui ne sont pas gérées.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-104">These examples show how to use the `My.Application.Log.WriteException` method to log exceptions that you catch explicitly and exceptions that are unhandled.</span></span>  
  
 <span data-ttu-id="5ec2d-105">Pour enregistrer des informations de traçage, utilisez la méthode `My.Application.Log.WriteEntry`.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-105">For logging tracing information, use the `My.Application.Log.WriteEntry` method.</span></span> <span data-ttu-id="5ec2d-106">Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="5ec2d-106">For more information, see <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>  
  
### <a name="to-log-a-handled-exception"></a><span data-ttu-id="5ec2d-107">Pour enregistrer une exception gérée</span><span class="sxs-lookup"><span data-stu-id="5ec2d-107">To log a handled exception</span></span>  
  
1.  <span data-ttu-id="5ec2d-108">Créez la méthode qui génère les informations sur l’exception.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-108">Create the method that will generate the exception information.</span></span>  
  
     <span data-ttu-id="5ec2d-109">[!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ec2d-109">[!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]</span></span>  
  
2.  <span data-ttu-id="5ec2d-110">Utilisez un bloc `Try...Catch` pour intercepter l’exception.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-110">Use a `Try...Catch` block to catch the exception.</span></span>  
  
     <span data-ttu-id="5ec2d-111">[!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ec2d-111">[!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]</span></span>  
  
3.  <span data-ttu-id="5ec2d-112">Placez le code susceptible de générer une exception dans le bloc `Try`.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-112">Put the code that could generate an exception in the `Try` block.</span></span>  
  
     <span data-ttu-id="5ec2d-113">Supprimez les commentaires des lignes `Dim` et `MsgBox` pour déclencher une exception <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-113">Uncomment the `Dim` and `MsgBox` lines to cause a <xref:System.NullReferenceException> exception.</span></span>  
  
     <span data-ttu-id="5ec2d-114">[!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ec2d-114">[!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]</span></span>  
  
4.  <span data-ttu-id="5ec2d-115">Dans le bloc `Catch`, utilisez la méthode `My.Application.Log.WriteException` pour écrire les informations sur l’exception.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-115">In the `Catch` block, use the `My.Application.Log.WriteException` method to write the exception information.</span></span>  
  
     <span data-ttu-id="5ec2d-116">[!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ec2d-116">[!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]</span></span>  
  
     <span data-ttu-id="5ec2d-117">L’exemple suivant montre le code complet permettant d’enregistrer une exception gérée.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-117">The following example shows the complete code for logging a handled exception.</span></span>  
  
     <span data-ttu-id="5ec2d-118">[!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ec2d-118">[!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]</span></span>  
  
### <a name="to-log-an-unhandled-exception"></a><span data-ttu-id="5ec2d-119">Pour enregistrer une exception non gérée</span><span class="sxs-lookup"><span data-stu-id="5ec2d-119">To log an unhandled exception</span></span>  
  
1.  <span data-ttu-id="5ec2d-120">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-120">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="5ec2d-121">Dans le menu **Projet** , choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-121">On the **Project** menu, choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="5ec2d-122">Cliquez sur l’onglet **Application** .</span><span class="sxs-lookup"><span data-stu-id="5ec2d-122">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="5ec2d-123">Cliquez sur le bouton **Afficher les événements de l’application** pour ouvrir l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-123">Click the **View Application Events** button to open the Code Editor.</span></span>  
  
     <span data-ttu-id="5ec2d-124">Le fichier ApplicationEvents.vb s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-124">This opens the ApplicationEvents.vb file.</span></span>  
  
4.  <span data-ttu-id="5ec2d-125">Ouvrez le fichier ApplicationEvents.vb dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-125">Have the ApplicationEvents.vb file open in the Code Editor.</span></span> <span data-ttu-id="5ec2d-126">Dans le menu **Général** , choisissez **Événements MyApplication**.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-126">On the **General** menu, choose **MyApplication Events**.</span></span>  
  
5.  <span data-ttu-id="5ec2d-127">Dans le menu **Déclarations**, choisissez **UnhandledException**.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-127">On the **Declarations** menu, choose **UnhandledException**.</span></span>  
  
     <span data-ttu-id="5ec2d-128">L’application déclenche l’événement <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> avant l’exécution de l’application principale.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-128">The application raises the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> event before the main application runs.</span></span>  
  
6.  <span data-ttu-id="5ec2d-129">Ajoutez la méthode `My.Application.Log.WriteException` au gestionnaire d’événements `UnhandledException` .</span><span class="sxs-lookup"><span data-stu-id="5ec2d-129">Add the `My.Application.Log.WriteException` method to the `UnhandledException` event handler.</span></span>  
  
     <span data-ttu-id="5ec2d-130">[!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ec2d-130">[!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]</span></span>  
  
     <span data-ttu-id="5ec2d-131">L’exemple suivant montre le code complet permettant d’enregistrer une exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="5ec2d-131">The following example shows the complete code for logging an unhandled exception.</span></span>  
  
     <span data-ttu-id="5ec2d-132">[!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="5ec2d-132">[!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ec2d-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ec2d-133">See Also</span></span>  
 <span data-ttu-id="5ec2d-134"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5ec2d-134"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="5ec2d-135"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span><span class="sxs-lookup"><span data-stu-id="5ec2d-135"><xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A></span></span>   
 <span data-ttu-id="5ec2d-136"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span><span class="sxs-lookup"><span data-stu-id="5ec2d-136"><xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A></span></span>   
 <span data-ttu-id="5ec2d-137">[Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="5ec2d-137">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 <span data-ttu-id="5ec2d-138">[Guide pratique pour écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span><span class="sxs-lookup"><span data-stu-id="5ec2d-138">[How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span></span>  
 <span data-ttu-id="5ec2d-139">[Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span><span class="sxs-lookup"><span data-stu-id="5ec2d-139">[Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md) </span></span>  
 [<span data-ttu-id="5ec2d-140">Procédure pas à pas : modification de l’emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="5ec2d-140">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)

