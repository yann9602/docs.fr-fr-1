---
title: Enregistrement d'informations provenant de l'application (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Log object
- My.Log object
- applications [Visual Basic], logging information from
- logging
- My.Application.Log object
- examples [Visual Basic], logging application information
ms.assetid: 8bf4f047-22d6-48d6-aec5-93b98ad5b8e8
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e52aaf4c26b4fa60ee04d7df6aa96980ebbf491
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="logging-information-from-the-application-visual-basic"></a><span data-ttu-id="f041a-102">Enregistrement d'informations provenant de l'application (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f041a-102">Logging Information from the Application (Visual Basic)</span></span>
<span data-ttu-id="f041a-103">Cette section contient des rubriques sur l’enregistrement d’informations provenant de l’application à l’aide de l’objet `My.Application.Log` ou `My.Log`, et sur l’extension des fonctionnalités de journalisation de l’application.</span><span class="sxs-lookup"><span data-stu-id="f041a-103">This section contains topics that cover how to log information from your application using the `My.Application.Log` or `My.Log` object, and how to extend the application's logging capabilities.</span></span>  
  
 <span data-ttu-id="f041a-104">L’objet `Log` fournit des méthodes pour écrire des informations dans les écouteurs de journalisation de l’application, et la propriété `TraceSource` avancée de l’objet `Log` fournit des informations de configuration détaillées.</span><span class="sxs-lookup"><span data-stu-id="f041a-104">The `Log` object provides methods for writing information to the application's log listeners, and the `Log` object's advanced `TraceSource` property provides detailed configuration information.</span></span> <span data-ttu-id="f041a-105">L’objet `Log` est configuré par le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="f041a-105">The `Log` object is configured by the application's configuration file.</span></span>  
  
 <span data-ttu-id="f041a-106">L’objet `My.Log` est disponible uniquement pour les applications ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f041a-106">The `My.Log` object is available only for ASP.NET applications.</span></span> <span data-ttu-id="f041a-107">Pour les applications clientes, utilisez `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="f041a-107">For client applications, use `My.Application.Log`.</span></span> <span data-ttu-id="f041a-108">Pour plus d'informations, consultez <xref:Microsoft.VisualBasic.Logging.Log>.</span><span class="sxs-lookup"><span data-stu-id="f041a-108">For more information, see <xref:Microsoft.VisualBasic.Logging.Log>.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="f041a-109">Tâches</span><span class="sxs-lookup"><span data-stu-id="f041a-109">Tasks</span></span>  
  
|<span data-ttu-id="f041a-110">Pour</span><span class="sxs-lookup"><span data-stu-id="f041a-110">To</span></span>|<span data-ttu-id="f041a-111">Voir</span><span class="sxs-lookup"><span data-stu-id="f041a-111">See</span></span>|  
|--------|---------|  
|<span data-ttu-id="f041a-112">Écrire des informations sur les événements dans les journaux de l’application.</span><span class="sxs-lookup"><span data-stu-id="f041a-112">Write event information to the application's logs.</span></span>|[<span data-ttu-id="f041a-113">Guide pratique : écrire des messages de journal</span><span class="sxs-lookup"><span data-stu-id="f041a-113">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)|  
|<span data-ttu-id="f041a-114">Écrire des informations sur les exceptions dans les journaux de l’application.</span><span class="sxs-lookup"><span data-stu-id="f041a-114">Write exception information to the application's logs.</span></span>|[<span data-ttu-id="f041a-115">Guide pratique : enregistrer des exceptions</span><span class="sxs-lookup"><span data-stu-id="f041a-115">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)|  
|<span data-ttu-id="f041a-116">Écrire des informations de traçage dans les journaux de l’application quand l’application démarre et s’arrête.</span><span class="sxs-lookup"><span data-stu-id="f041a-116">Write trace information to the application's logs when the application starts and shuts down.</span></span>|[<span data-ttu-id="f041a-117">Guide pratique : enregistrer des messages quand l’application démarre ou s’arrête</span><span class="sxs-lookup"><span data-stu-id="f041a-117">How to: Log Messages When the Application Starts or Shuts Down</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-messages-when-the-application-starts-or-shuts-down.md)|  
|<span data-ttu-id="f041a-118">Configurer `My.Application.Log` pour écrire des informations dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="f041a-118">Configure `My.Application.Log` to write information to a text file.</span></span>|[<span data-ttu-id="f041a-119">Guide pratique : écrire des informations sur des événements dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="f041a-119">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)|  
|<span data-ttu-id="f041a-120">Configurer `My.Application.Log` pour écrire des informations dans un journal des événements.</span><span class="sxs-lookup"><span data-stu-id="f041a-120">Configure `My.Application.Log` to write information to an event log.</span></span>|[<span data-ttu-id="f041a-121">Guide pratique : écrire dans le journal des événements de l’application</span><span class="sxs-lookup"><span data-stu-id="f041a-121">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)|  
|<span data-ttu-id="f041a-122">Changer l’emplacement où `My.Application.Log` écrit les informations.</span><span class="sxs-lookup"><span data-stu-id="f041a-122">Change where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="f041a-123">Procédure pas à pas : modification de l’emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="f041a-123">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="f041a-124">Déterminer l’emplacement où `My.Application.Log` écrit les informations.</span><span class="sxs-lookup"><span data-stu-id="f041a-124">Determine where `My.Application.Log` writes information.</span></span>|[<span data-ttu-id="f041a-125">Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="f041a-125">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)|  
|<span data-ttu-id="f041a-126">Créer un écouteur de journalisation personnalisé pour `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="f041a-126">Create a custom log listener for `My.Application.Log`.</span></span>|[<span data-ttu-id="f041a-127">Procédure pas à pas : création d’écouteurs de journalisation personnalisés</span><span class="sxs-lookup"><span data-stu-id="f041a-127">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)|  
|<span data-ttu-id="f041a-128">Filtrer la sortie des journaux `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="f041a-128">Filter the output of the `My.Application.Log` logs.</span></span>|[<span data-ttu-id="f041a-129">Procédure pas à pas : filtrage de la sortie de My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="f041a-129">Walkthrough: Filtering My.Application.Log Output</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md)|  
  
## <a name="see-also"></a><span data-ttu-id="f041a-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f041a-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="f041a-131">Utilisation des journaux des applications</span><span class="sxs-lookup"><span data-stu-id="f041a-131">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="f041a-132">Dépannage : écouteurs de journalisation</span><span class="sxs-lookup"><span data-stu-id="f041a-132">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
