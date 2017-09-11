---
title: "Détermination de l’emplacement des informations My.Application.Log (Visual Basic)"
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
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
caps.latest.revision: 24
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
ms.openlocfilehash: 36c91f607a5a9d0dcf65ee6e049b9a49cdd37929
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="12b3d-102">Procédure pas à pas : détermination de l'emplacement des informations My.Application.Log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12b3d-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="12b3d-103">L’objet `My.Application.Log` peut écrire des informations dans plusieurs écouteurs de journalisation.</span><span class="sxs-lookup"><span data-stu-id="12b3d-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="12b3d-104">Les écouteurs de journalisation sont configurés par le fichier de configuration de l’ordinateur et peuvent être remplacés par un fichier de configuration d’une application.</span><span class="sxs-lookup"><span data-stu-id="12b3d-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="12b3d-105">Cette rubrique décrit les paramètres par défaut et explique comment déterminer les paramètres de votre application.</span><span class="sxs-lookup"><span data-stu-id="12b3d-105">This topic describes the default settings and how to determine the settings for your application.</span></span>  
  
 <span data-ttu-id="12b3d-106">Pour plus d’informations sur les emplacements de sortie par défaut, consultez [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="12b3d-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="12b3d-107">Pour déterminer les écouteurs de My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="12b3d-107">To determine the listeners for My.Application.Log</span></span>  
  
1.  <span data-ttu-id="12b3d-108">Recherchez le fichier de configuration de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="12b3d-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="12b3d-109">Si vous développez l’assembly, vous pouvez accéder au fichier app.config dans [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] à partir de l’ **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="12b3d-109">If you are developing the assembly, you can access the app.config in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] from the **Solution Explorer**.</span></span> <span data-ttu-id="12b3d-110">Sinon, le nom du fichier de configuration est le nom de l’assembly suivi de « .config ». Il se trouve dans le même répertoire que l’assembly.</span><span class="sxs-lookup"><span data-stu-id="12b3d-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12b3d-111">Tous les assemblys n’ont pas un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="12b3d-111">Not every assembly has a configuration file.</span></span>  
  
     <span data-ttu-id="12b3d-112">Le fichier de configuration est un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="12b3d-112">The configuration file is an XML file.</span></span>  
  
2.  <span data-ttu-id="12b3d-113">Recherchez la section `<listeners>` dans la section `<source>` avec l’attribut `name` « DefaultSource », qui se trouve dans la section `<sources>` .</span><span class="sxs-lookup"><span data-stu-id="12b3d-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="12b3d-114">La section `<sources>` se trouve dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="12b3d-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
     <span data-ttu-id="12b3d-115">Si ces sections n’existent pas, le fichier de configuration de l’ordinateur peut configurer les écouteurs de journalisation de `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="12b3d-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="12b3d-116">Les étapes suivantes décrivent comment déterminer ce que définit le fichier de configuration de l’ordinateur :</span><span class="sxs-lookup"><span data-stu-id="12b3d-116">The following steps describe how to determine what the computer configuration file defines:</span></span>  
  
    1.  <span data-ttu-id="12b3d-117">Recherchez le fichier machine.config de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="12b3d-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="12b3d-118">En règle générale, il se trouve dans le répertoire *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* , où `SystemRoot` est le répertoire du système d’exploitation et `frameworkVersion` est la version du [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12b3d-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
         <span data-ttu-id="12b3d-119">Les paramètres de machine.config peuvent être remplacés par le fichier de configuration d’une application.</span><span class="sxs-lookup"><span data-stu-id="12b3d-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>  
  
         <span data-ttu-id="12b3d-120">Si les éléments facultatifs répertoriés ci-dessous n’existent pas, vous pouvez les créer.</span><span class="sxs-lookup"><span data-stu-id="12b3d-120">If the optional elements listed below do not exist, you can create them.</span></span>  
  
    2.  <span data-ttu-id="12b3d-121">Recherchez la section `<listeners>` dans la section `<source>` avec l’attribut `name` « DefaultSource », dans la section `<sources>` , dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="12b3d-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
         <span data-ttu-id="12b3d-122">Si ces sections n’existent pas, `My.Application.Log` a seulement les écouteurs de journalisation par défaut.</span><span class="sxs-lookup"><span data-stu-id="12b3d-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>  
  
3.  <span data-ttu-id="12b3d-123">Recherchez les éléments <`add>` dans la section <`listeners>`.</span><span class="sxs-lookup"><span data-stu-id="12b3d-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>  
  
     <span data-ttu-id="12b3d-124">Ces éléments ajoutent les écouteurs de journalisation nommés à la source de `My.Application.Log` .</span><span class="sxs-lookup"><span data-stu-id="12b3d-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>  
  
4.  <span data-ttu-id="12b3d-125">Recherchez les éléments `<add>` avec les noms des écouteurs de journalisation dans la `<sharedListeners>` section, dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="12b3d-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="12b3d-126">Pour de nombreux types d’écouteurs partagés, les données d’initialisation de l’écouteur comprennent une description de l’endroit où l’écouteur dirige les données :</span><span class="sxs-lookup"><span data-stu-id="12b3d-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>  
  
    -   <span data-ttu-id="12b3d-127">Un écouteur <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=fullName> écrit dans un fichier journal, comme décrit dans l’introduction.</span><span class="sxs-lookup"><span data-stu-id="12b3d-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=fullName> listener writes to a file log, as described in the introduction.</span></span>  
  
    -   <span data-ttu-id="12b3d-128">Un écouteur <xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName> écrit les informations dans le journal des événements de l’ordinateur spécifié par le paramètre `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="12b3d-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=fullName> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="12b3d-129">Pour afficher un journal des événements, vous pouvez utiliser l’ **Explorateur de serveurs** ou l’ **Observateur d’événements Windows**.</span><span class="sxs-lookup"><span data-stu-id="12b3d-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="12b3d-130">Pour plus d'informations, consultez [ETW Events in the .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299).</span><span class="sxs-lookup"><span data-stu-id="12b3d-130">For more information, see [ETW Events in the .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299).</span></span>  
  
    -   <span data-ttu-id="12b3d-131">Les écouteurs <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=fullName> et <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=fullName> écrivent dans le fichier spécifié par le paramètre `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="12b3d-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=fullName> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=fullName> listeners write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="12b3d-132">Un écouteur <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=fullName> écrit dans la console de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="12b3d-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=fullName> listener writes to the command-line console.</span></span>  
  
    -   <span data-ttu-id="12b3d-133">Pour plus d’informations sur les emplacements où d’autres types d’écouteurs de journalisation écrivent les informations, consultez la documentation de ce type.</span><span class="sxs-lookup"><span data-stu-id="12b3d-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b3d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12b3d-134">See Also</span></span>  
 <span data-ttu-id="12b3d-135"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="12b3d-135"><xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName></span></span>   
 <span data-ttu-id="12b3d-136"><xref:System.Diagnostics.DefaultTraceListener></span><span class="sxs-lookup"><span data-stu-id="12b3d-136"><xref:System.Diagnostics.DefaultTraceListener></span></span>   
 <span data-ttu-id="12b3d-137"><xref:System.Diagnostics.EventLogTraceListener></span><span class="sxs-lookup"><span data-stu-id="12b3d-137"><xref:System.Diagnostics.EventLogTraceListener></span></span>   
 <span data-ttu-id="12b3d-138"><xref:System.Diagnostics.DelimitedListTraceListener></span><span class="sxs-lookup"><span data-stu-id="12b3d-138"><xref:System.Diagnostics.DelimitedListTraceListener></span></span>   
 <span data-ttu-id="12b3d-139"><xref:System.Diagnostics.XmlWriterTraceListener></span><span class="sxs-lookup"><span data-stu-id="12b3d-139"><xref:System.Diagnostics.XmlWriterTraceListener></span></span>   
 <span data-ttu-id="12b3d-140"><xref:System.Diagnostics.ConsoleTraceListener></span><span class="sxs-lookup"><span data-stu-id="12b3d-140"><xref:System.Diagnostics.ConsoleTraceListener></span></span>   
 <span data-ttu-id="12b3d-141"><xref:System.Diagnostics></span><span class="sxs-lookup"><span data-stu-id="12b3d-141"><xref:System.Diagnostics></span></span>   
 <span data-ttu-id="12b3d-142">[Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span><span class="sxs-lookup"><span data-stu-id="12b3d-142">[Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md) </span></span>  
 <span data-ttu-id="12b3d-143">[Guide pratique pour enregistrer des exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span><span class="sxs-lookup"><span data-stu-id="12b3d-143">[How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md) </span></span>  
 <span data-ttu-id="12b3d-144">[Guide pratique pour écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span><span class="sxs-lookup"><span data-stu-id="12b3d-144">[How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) </span></span>  
 <span data-ttu-id="12b3d-145">[Procédure pas à pas : modification de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md) </span><span class="sxs-lookup"><span data-stu-id="12b3d-145">[Walkthrough: Changing Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md) </span></span>  
 <span data-ttu-id="12b3d-146">[Événements ETW dans le .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299) </span><span class="sxs-lookup"><span data-stu-id="12b3d-146">[ETW Events in the .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299) </span></span>  
 [<span data-ttu-id="12b3d-147">Dépannage : écouteurs de journalisation</span><span class="sxs-lookup"><span data-stu-id="12b3d-147">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)

