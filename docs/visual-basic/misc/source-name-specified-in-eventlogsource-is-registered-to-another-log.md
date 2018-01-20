---
title: "Le nom de source spécifié dans le journal est inscrit auprès d’un journal autre que celui spécifié dans EventLogName"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0a100789486dda403f483489e73accbf219374c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a><span data-ttu-id="5d49c-102">Le nom de source spécifié dans le journal est inscrit auprès d’un journal autre que celui spécifié dans EventLogName</span><span class="sxs-lookup"><span data-stu-id="5d49c-102">Source name specified in EventLogSource is registered to a log other than that specified in EventLogName</span></span>
<span data-ttu-id="5d49c-103">Le `EventLog` essaie de faire référence à une source qui est inscrite auprès d’un autre journal.</span><span class="sxs-lookup"><span data-stu-id="5d49c-103">The `EventLog` is attempting to refer to a source that is registered to a different log.</span></span> <span data-ttu-id="5d49c-104">Si vous écrivez des entrées dans le journal des événements, vous devez spécifier la propriété <xref:System.Diagnostics.EventLog.Source%2A> .</span><span class="sxs-lookup"><span data-stu-id="5d49c-104">If you are writing entries to an event log, you must specify the <xref:System.Diagnostics.EventLog.Source%2A> property.</span></span> <span data-ttu-id="5d49c-105">La propriété <xref:System.Diagnostics.EventLog.Source%2A> inscrit votre composant auprès du journal des événements comme source d’entrées valide.</span><span class="sxs-lookup"><span data-stu-id="5d49c-105">The <xref:System.Diagnostics.EventLog.Source%2A> property registers your component with the event log as a valid source of entries.</span></span> <span data-ttu-id="5d49c-106">Une même source ne peut être associée (et donc écrire des entrées) qu’à un seul journal des événements à la fois.</span><span class="sxs-lookup"><span data-stu-id="5d49c-106">A single source can be associated with (and therefore write entries to) only one event log at a time.</span></span>  
  
 <span data-ttu-id="5d49c-107">Par défaut, si vous tentez d’écrire une entrée sans avoir d’abord inscrit votre composant en tant que source valide, le système inscrit automatiquement la source auprès du journal des événements, en utilisant la valeur de la propriété <xref:System.Diagnostics.EventLog.Source%2A> comme chaîne source.</span><span class="sxs-lookup"><span data-stu-id="5d49c-107">By default, if you try to write an entry without first having registered your component as a valid source, the system automatically registers the source with the event log, using the value of the <xref:System.Diagnostics.EventLog.Source%2A> property as the source string.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5d49c-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="5d49c-108">To correct this error</span></span>  
  
-   <span data-ttu-id="5d49c-109">Vérifiez que la source est inscrite auprès du journal approprié.</span><span class="sxs-lookup"><span data-stu-id="5d49c-109">Make sure the source is registered to the correct log.</span></span> <span data-ttu-id="5d49c-110">Pour ce faire, utilisez la méthode <xref:System.Diagnostics.EventLog.CreateEventSource%2A> ou l’une de ses surcharges pour spécifier une chaîne qui identifie votre composant auprès du journal des événements.</span><span class="sxs-lookup"><span data-stu-id="5d49c-110">To do this, use the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method or one of its overloads to specify a string that uniquely identifies your component to the event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d49c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d49c-111">See Also</span></span>  
 [<span data-ttu-id="5d49c-112">Administration des journaux des événements</span><span class="sxs-lookup"><span data-stu-id="5d49c-112">Administering Event Logs</span></span>](http://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [<span data-ttu-id="5d49c-113">Références du journal des événements</span><span class="sxs-lookup"><span data-stu-id="5d49c-113">Event Log References</span></span>](http://msdn.microsoft.com/library/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [<span data-ttu-id="5d49c-114">Comment : ajouter votre Application en tant que Source d’entrées de journal des événements</span><span class="sxs-lookup"><span data-stu-id="5d49c-114">How to: Add Your Application as a Source of Event Log Entries</span></span>](http://msdn.microsoft.com/library/948ff920-a739-4e66-a191-ee951512d42c)  
 [<span data-ttu-id="5d49c-115">Comment : supprimer une Source d’événement</span><span class="sxs-lookup"><span data-stu-id="5d49c-115">How to: Remove an Event Source</span></span>](http://msdn.microsoft.com/library/bc66c900-4b8a-426a-b8e2-17031a20167e)
