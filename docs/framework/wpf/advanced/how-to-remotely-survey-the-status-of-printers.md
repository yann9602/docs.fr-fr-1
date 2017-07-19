---
title: "Comment&#160;: observer &#224; distance l&#39;&#233;tat d&#39;imprimantes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "état de l'imprimante, observer à distance"
  - "observer à distance l'état de l'imprimante"
  - "statut, imprimantes, observer à distance"
  - "observer à distance l'état de l'imprimante"
ms.assetid: d6324759-8292-4c23-9584-9c708887dc94
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: observer &#224; distance l&#39;&#233;tat d&#39;imprimantes
Dans les petites et grandes entreprises, il peut arriver que plusieurs imprimantes ne fonctionnent pas en raison d'un problème \(bourrage papier, plus de papier ou autre\).  Les nombreuses propriétés d'imprimante proposées dans les [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] de [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] permettent d'observer rapidement l'état des imprimantes.  
  
## Exemple  
 Les étapes principales pour créer ce type d'utilitaire sont les suivantes :  
  
1.  Obtenir une liste de tous les serveurs d'impression.  
  
2.  Parcourir les serveurs pour interroger leurs files d'attente à l'impression.  
  
3.  À chaque exploration du serveur, parcourir toutes les files d'attente et lire chaque propriété qui pourrait indiquer que la file d'attente ne fonctionne pas actuellement.  
  
 Une série d'extraits de code est présentée ci\-dessous.  Pour des raisons de simplicité, cet exemple suppose qu'il existe une liste de serveurs d'impression délimitée par CRLF.  La variable `fileOfPrintServers` est un objet <xref:System.IO.StreamReader> pour ce fichier.  Étant donné que chaque nom de serveur figure sur sa propre ligne, tout appel de <xref:System.IO.StreamReader.ReadLine%2A> obtient le nom du serveur suivant et déplace le curseur du <xref:System.IO.StreamReader> au début de la ligne suivante.  
  
 Dans la boucle externe, le code crée un objet <xref:System.Printing.PrintServer> pour le tout dernier serveur d'impression et spécifie que l'application doit disposer de droits d'administration sur le serveur.  
  
> [!NOTE]
>  S'il existe un grand nombre de serveurs, vous pouvez améliorer les performances en utilisant les constructeurs [PrintServer\(String, String\<xref:System.Printing.PrintServer.%23ctor%28System.String%2CSystem.String%5B%5D%2CSystem.Printing.PrintSystemDesiredAccess%29> qui initialisent uniquement les propriétés dont vous avez besoin.  
  
 L'exemple utilise ensuite <xref:System.Printing.PrintServer.GetPrintQueues%2A> pour créer une collection de toutes les files d'attente du serveur et commence à les parcourir en boucle.  La boucle interne contient une structure de branches qui correspond aux deux façons de vérifier l'état d'une imprimante :  
  
-   Vous pouvez lire les indicateurs de la propriété <xref:System.Printing.PrintQueue.QueueStatus%2A> qui est du type <xref:System.Printing.PrintQueueStatus>.  
  
-   Vous pouvez lire chaque propriété appropriée telle que <xref:System.Printing.PrintQueue.IsOutOfPaper%2A> et <xref:System.Printing.PrintQueue.IsPaperJammed%2A>.  
  
 Cet exemple illustrant les deux méthodes, l'utilisateur a été auparavant invité à choisir une méthode et a indiqué qu'il souhaitait utiliser les indicateurs de la propriété <xref:System.Printing.PrintQueue.QueueStatus%2A>.  Voir ci\-dessous pour des informations détaillées sur les deux méthodes.  
  
 Enfin, les résultats sont présentés à l'utilisateur.  
  
 [!code-cpp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#surveyqueues)]
 [!code-csharp[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#surveyqueues)]
 [!code-vb[PrinterStatusSurvey#SurveyQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#surveyqueues)]  
  
 Pour vérifier l'état de l'imprimante au moyen des indicateurs de la propriété <xref:System.Printing.PrintQueue.QueueStatus%2A>, vous contrôlez si chaque indicateur correspondant est défini.  La procédure standard pour vérifier si l'un des bits d'un ensemble de bits indicateurs est défini consiste à effectuer une opération AND logique en spécifiant l'ensemble d'indicateurs comme premier opérande et l'indicateur lui\-même comme deuxième opérande.  Comme l'indicateur lui\-même n'a qu'un seul bit défini, le résultat du AND logique est que, au plus, ce même bit est défini.  Pour déterminer si c'est le cas ou non, il suffit de comparer le résultat du AND logique à l'indicateur lui\-même.  Pour plus d'informations, consultez <xref:System.Printing.PrintQueueStatus>, [&, opérateur \(référence C\#\)](../Topic/&%20Operator%20\(C%23%20Reference\).md) et <xref:System.FlagsAttribute>.  
  
 Pour chaque attribut dont le bit est défini, le code ajoute une information préalable au rapport final qui sera présenté à l'utilisateur.  \(La méthode **ReportAvailabilityAtThisTime** qui est appelée à la fin du code est présentée ci\-après.\)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueattributes)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueattributes)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueattributes)]  
  
 Pour vérifier l'état de l'imprimante à l'aide de chaque propriété, il vous suffit de lire chaque propriété et d'ajouter une note au rapport final qui sera présenté à l'utilisateur si cette propriété a la valeur `true`.  \(La méthode **ReportAvailabilityAtThisTime** qui est appelée à la fin du code est présentée ci\-après.\)  
  
 [!code-cpp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#spottroubleusingqueueproperties)]
 [!code-csharp[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#spottroubleusingqueueproperties)]
 [!code-vb[PrinterStatusSurvey#SpotTroubleUsingQueueProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#spottroubleusingqueueproperties)]  
  
 La méthode **ReportAvailabilityAtThisTime** a été créée pour le cas où vous auriez besoin de déterminer si la file d'attente est disponible actuellement.  
  
 La méthode n'effectuera aucune action si les propriétés <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> et <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> sont égales. En effet, dans ce cas, l'imprimante est constamment disponible.  Si elles diffèrent, la méthode obtient l'heure actuelle qui doit alors être convertie en nombre total de minutes après minuit, car les propriétés <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> et <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> sont des <xref:System.Int32> représentant les minutes après minuit et non des objets <xref:System.DateTime>.  Enfin, la méthode vérifie si l'heure actuelle est située entre les heures de début et de fin.  
  
 [!code-cpp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PrinterStatusSurvey/CPP/Program.cpp#usingstartanduntiltimes)]
 [!code-csharp[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrinterStatusSurvey/CSharp/Program.cs#usingstartanduntiltimes)]
 [!code-vb[PrinterStatusSurvey#UsingStartAndUntilTimes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrinterStatusSurvey/visualbasic/program.vb#usingstartanduntiltimes)]  
  
## Voir aussi  
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
 [&, opérateur \(référence C\#\)](../Topic/&%20Operator%20\(C%23%20Reference\).md)   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Vue d'ensemble de l'impression](../../../../docs/framework/wpf/advanced/printing-overview.md)