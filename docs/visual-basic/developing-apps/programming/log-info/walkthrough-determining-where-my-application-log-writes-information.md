---
title: "Détermination de l’emplacement des informations My.Application.Log (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f35a850a262e96762b4ada3fdff1f14634f77317
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="b62f7-102">Procédure pas à pas : détermination de l'emplacement des informations My.Application.Log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b62f7-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="b62f7-103">L’objet `My.Application.Log` peut écrire des informations dans plusieurs écouteurs de journalisation.</span><span class="sxs-lookup"><span data-stu-id="b62f7-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="b62f7-104">Les écouteurs de journalisation sont configurés par le fichier de configuration de l’ordinateur et peuvent être remplacés par un fichier de configuration d’une application.</span><span class="sxs-lookup"><span data-stu-id="b62f7-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="b62f7-105">Cette rubrique décrit les paramètres par défaut et explique comment déterminer les paramètres de votre application.</span><span class="sxs-lookup"><span data-stu-id="b62f7-105">This topic describes the default settings and how to determine the settings for your application.</span></span>  
  
 <span data-ttu-id="b62f7-106">Pour plus d’informations sur les emplacements de sortie par défaut, consultez [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="b62f7-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="b62f7-107">Pour déterminer les écouteurs de My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="b62f7-107">To determine the listeners for My.Application.Log</span></span>  
  
1.  <span data-ttu-id="b62f7-108">Recherchez le fichier de configuration de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b62f7-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="b62f7-109">Si vous développez l’assembly, vous pouvez accéder au fichier app.config dans [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] à partir de l’ **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="b62f7-109">If you are developing the assembly, you can access the app.config in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] from the **Solution Explorer**.</span></span> <span data-ttu-id="b62f7-110">Sinon, le nom du fichier de configuration est le nom de l’assembly suivi de « .config ». Il se trouve dans le même répertoire que l’assembly.</span><span class="sxs-lookup"><span data-stu-id="b62f7-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b62f7-111">Tous les assemblys n’ont pas un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="b62f7-111">Not every assembly has a configuration file.</span></span>  
  
     <span data-ttu-id="b62f7-112">Le fichier de configuration est un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="b62f7-112">The configuration file is an XML file.</span></span>  
  
2.  <span data-ttu-id="b62f7-113">Recherchez la section `<listeners>` dans la section `<source>` avec l’attribut `name` « DefaultSource », qui se trouve dans la section `<sources>` .</span><span class="sxs-lookup"><span data-stu-id="b62f7-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="b62f7-114">La section `<sources>` se trouve dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="b62f7-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
     <span data-ttu-id="b62f7-115">Si ces sections n’existent pas, le fichier de configuration de l’ordinateur peut configurer les écouteurs de journalisation de `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="b62f7-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="b62f7-116">Les étapes suivantes décrivent comment déterminer ce que définit le fichier de configuration de l’ordinateur :</span><span class="sxs-lookup"><span data-stu-id="b62f7-116">The following steps describe how to determine what the computer configuration file defines:</span></span>  
  
    1.  <span data-ttu-id="b62f7-117">Recherchez le fichier machine.config de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b62f7-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="b62f7-118">En règle générale, il se trouve dans le répertoire *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* , où `SystemRoot` est le répertoire du système d’exploitation et `frameworkVersion` est la version du [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b62f7-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
         <span data-ttu-id="b62f7-119">Les paramètres de machine.config peuvent être remplacés par le fichier de configuration d’une application.</span><span class="sxs-lookup"><span data-stu-id="b62f7-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>  
  
         <span data-ttu-id="b62f7-120">Si les éléments facultatifs répertoriés ci-dessous n’existent pas, vous pouvez les créer.</span><span class="sxs-lookup"><span data-stu-id="b62f7-120">If the optional elements listed below do not exist, you can create them.</span></span>  
  
    2.  <span data-ttu-id="b62f7-121">Recherchez la section `<listeners>` dans la section `<source>` avec l’attribut `name` « DefaultSource », dans la section `<sources>` , dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="b62f7-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
         <span data-ttu-id="b62f7-122">Si ces sections n’existent pas, `My.Application.Log` a seulement les écouteurs de journalisation par défaut.</span><span class="sxs-lookup"><span data-stu-id="b62f7-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>  
  
3.  <span data-ttu-id="b62f7-123">Recherchez les éléments <`add>` dans la section <`listeners>`.</span><span class="sxs-lookup"><span data-stu-id="b62f7-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>  
  
     <span data-ttu-id="b62f7-124">Ces éléments ajoutent les écouteurs de journalisation nommés à la source de `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="b62f7-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>  
  
4.  <span data-ttu-id="b62f7-125">Recherchez les éléments `<add>` avec les noms des écouteurs de journalisation dans la `<sharedListeners>` section, dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="b62f7-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="b62f7-126">Pour de nombreux types d’écouteurs partagés, les données d’initialisation de l’écouteur comprennent une description de l’endroit où l’écouteur dirige les données :</span><span class="sxs-lookup"><span data-stu-id="b62f7-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>  
  
    -   <span data-ttu-id="b62f7-127">Un écouteur <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> écrit dans un fichier journal, comme décrit dans l’introduction.</span><span class="sxs-lookup"><span data-stu-id="b62f7-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>  
  
    -   <span data-ttu-id="b62f7-128">Un écouteur <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> écrit les informations dans le journal des événements de l’ordinateur spécifié par le paramètre `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="b62f7-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="b62f7-129">Pour afficher un journal des événements, vous pouvez utiliser l’ **Explorateur de serveurs** ou l’ **Observateur d’événements Windows**.</span><span class="sxs-lookup"><span data-stu-id="b62f7-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="b62f7-130">Pour plus d'informations, consultez [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="b62f7-130">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>  
  
    -   <span data-ttu-id="b62f7-131">Les écouteurs <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> et <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> écrivent dans le fichier spécifié par le paramètre `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="b62f7-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="b62f7-132">Un écouteur <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> écrit dans la console de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="b62f7-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>  
  
    -   <span data-ttu-id="b62f7-133">Pour plus d’informations sur les emplacements où d’autres types d’écouteurs de journalisation écrivent les informations, consultez la documentation de ce type.</span><span class="sxs-lookup"><span data-stu-id="b62f7-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b62f7-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b62f7-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DelimitedListTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics>  
 [<span data-ttu-id="b62f7-135">Utilisation des journaux des applications</span><span class="sxs-lookup"><span data-stu-id="b62f7-135">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="b62f7-136">Guide pratique : enregistrer des exceptions</span><span class="sxs-lookup"><span data-stu-id="b62f7-136">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="b62f7-137">Guide pratique : écrire des messages de journal</span><span class="sxs-lookup"><span data-stu-id="b62f7-137">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="b62f7-138">Procédure pas à pas : modification de l’emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="b62f7-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="b62f7-139">Événements ETW dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b62f7-139">ETW Events in the .NET Framework</span></span>](../../../../framework/performance/etw-events.md)  
 [<span data-ttu-id="b62f7-140">Dépannage : écouteurs de journalisation</span><span class="sxs-lookup"><span data-stu-id="b62f7-140">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)
