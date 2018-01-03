---
title: "Impossible d’obtenir un flux pour le journal"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dba511ecd2a5c050fc2c037ac437e38715609e95
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="daccd-102">Impossible d’obtenir un flux pour le journal</span><span class="sxs-lookup"><span data-stu-id="daccd-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="daccd-103">Impossible d’obtenir un flux pour le journal.</span><span class="sxs-lookup"><span data-stu-id="daccd-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="daccd-104">Les noms de fichiers potentiels basés sur \<nom > sont déjà en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="daccd-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="daccd-105">Le <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe ne peut pas créer un nouveau fichier journal étant donné que tous les noms de fichier journal potentiels basent sur \<nom > sont déjà en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="daccd-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="daccd-106">Un nombre trop élevé de fichiers journaux peut indiquer un problème architectural avec l’application.</span><span class="sxs-lookup"><span data-stu-id="daccd-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="daccd-107">Pour plus d’informations, consultez la documentation de la classe <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="daccd-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="daccd-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="daccd-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="daccd-109">Affectez à la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> la valeur <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> ou <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> pour inclure un horodatage dans le nom du fichier journal.</span><span class="sxs-lookup"><span data-stu-id="daccd-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="daccd-110">Archivez les journaux existants et supprimez-les de l’ordinateur pour permettre à l’objet <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> de créer des journaux.</span><span class="sxs-lookup"><span data-stu-id="daccd-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daccd-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daccd-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [<span data-ttu-id="daccd-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="daccd-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [<span data-ttu-id="daccd-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="daccd-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
