---
title: "Comment : observer à distance l'état d'imprimantes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- surveying printer status remotely [WPF]
- printer status [WPF], surveying remotely
- remotely surveying printer status [WPF]
- status [WPF], printers [WPF], surveying remotely
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ad824a1cef637edc99e6aaafc99d557167ea1f1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remotely-survey-the-status-of-printers"></a>Comment : observer à distance l'état d'imprimantes
Dans les moyennes et grandes entreprises, il peut arriver à tout moment que plusieurs imprimantes ne fonctionnent pas en raison d’un bourrage papier, d’un manque de papier ou d’un autre problème. L’ensemble complet de propriétés d’imprimante exposé dans les [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] de [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] permet de connaître rapidement l’état des imprimantes.  
  
## <a name="example"></a>Exemple  
 Voici les principales étapes à suivre pour créer ce type d’utilitaire.  
  
1.  Répertoriez l’ensemble des serveurs d’impression.  
  
2.  Parcourez les serveurs en boucle pour interroger leurs files d’attente à l’impression.  
  
3.  À chaque étape de la boucle de serveur, parcourez en boucle toutes les files d’attente du serveur et lisez chaque propriété pouvant indiquer que la file d’attente ne fonctionne pas actuellement.  
  
 Le code ci-dessous est une série d’extraits de code. Pour plus de simplicité, cet exemple suppose qu’il existe une liste de serveurs d’impression délimitée par des caractères CRLF (retour chariot-saut de ligne). La variable `fileOfPrintServers` est un <xref:System.IO.StreamReader> objet pour ce fichier. Étant donné que chaque nom de serveur se trouve sur sa propre ligne, tout appel de <xref:System.IO.StreamReader.ReadLine%2A> Obtient le nom du serveur suivant et déplace le <xref:System.IO.StreamReader>du curseur au début de la ligne suivante.  
  
 Dans la boucle externe, le code crée un <xref:System.Printing.PrintServer> de l’objet pour le dernier serveur d’impression et spécifie que l’application doit disposer des droits d’administration sur le serveur.  
  
> [!NOTE]
>  S’il existe un grand nombre de serveurs, vous pouvez améliorer les performances à l’aide de la <xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> constructeurs qui initialisent uniquement les propriétés que vous vous apprêtez à besoin.  
  
 L’exemple utilise ensuite <xref:System.Printing.PrintServer.GetPrintQueues%2A> créer une collection de tous les du serveur de files d’attente et commence à parcourir en boucle. La boucle interne contient une structure en branches correspondant aux deux méthodes de vérification de l’état de l’imprimante :  
  
-   Vous pouvez lire les indicateurs de le <xref:System.Printing.PrintQueue.QueueStatus%2A> propriété qui est de type <xref:System.Printing.PrintQueueStatus>.  
  
-   Vous pouvez lire chaque propriété appropriée tel que <xref:System.Printing.PrintQueue.IsOutOfPaper%2A>, et <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.  
  
 Cet exemple illustre les deux méthodes, l’utilisateur a été précédemment vous y êtes invité à choisir une méthode à utiliser et a répondu par « y », qu’il souhaitait utiliser les indicateurs de le <xref:System.Printing.PrintQueue.QueueStatus%2A> propriété. Voir ci-dessous pour obtenir des informations détaillées sur les deux méthodes.  
  
 Enfin, les résultats sont présentés à l’utilisateur.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Pour vérifier l’état de l’imprimante à l’aide des indicateurs de le <xref:System.Printing.PrintQueue.QueueStatus%2A> propriété, vous vérifiez chaque indicateur correspondant est défini. La méthode standard pour voir si un bit est défini dans un ensemble d’indicateurs binaires consiste à effectuer une opération AND logique en utilisant comme opérandes l’ensemble d’indicateurs et l’indicateur lui-même. Étant donné que l’indicateur lui-même n’a qu’un seul bit de défini, l’opération AND logique ne peut pas trouver plus d’un même bit défini. Pour savoir si c’est bien le cas, il suffit de comparer le résultat de l’opération AND logique avec l’indicateur lui-même. Pour plus d’informations, consultez <xref:System.Printing.PrintQueueStatus>, le [&, opérateur (référence c#)](~/docs/csharp/language-reference/operators/and-operator.md), et <xref:System.FlagsAttribute>.  
  
 Pour chaque attribut dont le bit est défini, le code ajoute une note au rapport final qui sera présenté à l’utilisateur. (La méthode **ReportAvailabilityAtThisTime** qui est appelée à la fin du code est présentée ci-après.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Pour vérifier l’état de l’imprimante à l’aide de chaque propriété, il vous suffit de lire chaque propriété et d’ajouter une note au rapport final qui sera présenté à l’utilisateur si la propriété est `true`. (La méthode **ReportAvailabilityAtThisTime** qui est appelée à la fin du code est présentée ci-après.)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 La méthode **ReportAvailabilityAtThisTime** a été créée au cas où vous devriez déterminer si la file d’attente est disponible à l’heure actuelle.  
  
 La méthode ne fonctionnera pas si le <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> et <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> les propriétés sont égales ; car dans ce cas l’imprimante est disponible en permanence. Si elles sont différentes, la méthode obtient l’heure actuelle qui doit ensuite être convertie en nombre total de minutes après minuit, car le <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> et <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriétés sont <xref:System.Int32>représentant les minutes après minuit, ne pas <xref:System.DateTime> objets. Enfin, la méthode vérifie si l’heure actuelle se situe entre les heures de début et de fin.  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A>  
 <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A>  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintQueueStatus>  
 <xref:System.FlagsAttribute>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 [&, Opérateur (référence c#)](~/docs/csharp/language-reference/operators/and-operator.md)  
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Vue d’ensemble de l’impression](../../../../docs/framework/wpf/advanced/printing-overview.md)
