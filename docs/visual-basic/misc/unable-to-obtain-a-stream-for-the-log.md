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
ms.openlocfilehash: dd3051b2331502c9f4f3430bbf88731b307d1b1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a>Impossible d’obtenir un flux pour le journal
Impossible d’obtenir un flux pour le journal. Les noms de fichiers potentiels basés sur \<nom > sont déjà en cours d’utilisation.  
  
 Le <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> classe ne peut pas créer un nouveau fichier journal étant donné que tous les noms de fichier journal potentiels basent sur \<nom > sont déjà en cours d’utilisation.  
  
 Un nombre trop élevé de fichiers journaux peut indiquer un problème architectural avec l’application. Pour plus d’informations, consultez la documentation de la classe <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> .  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Affectez à la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> la valeur <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> ou <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> pour inclure un horodatage dans le nom du fichier journal.  
  
2.  Archivez les journaux existants et supprimez-les de l’ordinateur pour permettre à l’objet <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> de créer des journaux.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [My.Application.Log (objet)](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [My.Log (objet)](../../visual-basic/language-reference/objects/my-log-object.md)
