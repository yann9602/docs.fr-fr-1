---
title: "Comment&#160;: diagnostiquer un travail d&#39;impression probl&#233;matique | Microsoft Docs"
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
  - "travaux d'impression, diagnostiquer des problèmes"
  - "travaux d'impression, dépanner"
  - "dépanner les problèmes de travaux d'impression"
ms.assetid: b081a170-84c6-48f9-a487-5766a8d58a82
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Comment&#160;: diagnostiquer un travail d&#39;impression probl&#233;matique
Les administrateurs de réseaux reçoivent souvent des plaintes des utilisateurs à propos des travaux d'impression qui échouent ou sont trop lents.  Les très nombreuses propriétés de travail d'impression proposées dans les [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] de [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] permettent d'effectuer rapidement un diagnostic à distance des travaux d'impression.  
  
## Exemple  
 Les étapes principales pour créer ce type d'utilitaire sont les suivantes :  
  
1.  Identifier le travail d'impression dont se plaint l'utilisateur.  Souvent, les indications fournies par les utilisateurs ne sont pas très précises.  Ils ne connaissant pas nécessairement les noms de leurs serveurs d'impression ou imprimantes.  Ils peuvent décrire l'emplacement de l'imprimante avec une terminologie différente de celle utilisée dans la définition de la propriété <xref:System.Printing.PrintQueue.Location%2A>.  C'est pourquoi il est utile de générer une liste des travaux actuellement soumis par l'utilisateur.  Si plusieurs travaux sont en attente d'impression, la communication entre l'utilisateur et l'administrateur du système d'impression peut permettre de localiser le travail problématique.  Les sous\-étapes sont les suivantes :  
  
    1.  Obtenir une liste de tous les serveurs d'impression.  
  
    2.  Parcourir les serveurs pour interroger leurs files d'attente à l'impression.  
  
    3.  À chaque exploration du serveur, parcourir toutes les files d'attente de ce serveur pour interroger leurs travaux  
  
    4.  À chaque exploration de la file d'attente, parcourir ses travaux et rassembler des indications sur ceux soumis par l'utilisateur plaignant.  
  
2.  Une fois le travail d'impression problématique identifié, examiner les propriétés appropriées pour tenter de cerner le problème.  Par exemple, le travail est\-il en état d'erreur ou l'imprimante qui dessert la file d'attente a\-t\-elle été éteinte avant l'impression du travail ?  
  
 Vous trouverez ci\-dessous une série d'exemples de code.  Le premier exemple de code illustre le parcours des files d'attente à l'impression.  \(Étape 1c ci\-dessus.\) La variable `myPrintQueues` est l'objet <xref:System.Printing.PrintQueueCollection> pour le serveur d'impression actif.  
  
 L'exemple de code commence par actualiser l'objet de file d'attente à l'impression en utilisant <xref:System.Printing.PrintQueue.Refresh%2A?displayProperty=fullName>.  Cela garantit que les propriétés de l'objet représentent exactement l'état de l'imprimante physique correspondante.  L'application obtient ensuite l'ensemble des travaux d'impression actuellement placés dans la file d'attente à l'impression en utilisant <xref:System.Printing.PrintQueue.GetPrintJobInfoCollection%2A>.  
  
 Ensuite, l'application parcourt la collection <xref:System.Printing.PrintSystemJobInfo> et compare chaque propriété <xref:System.Printing.PrintSystemJobInfo.Submitter%2A> à l'alias de l'utilisateur plaignant.  Si ces éléments concordent, l'application ajoute les informations d'identification du travail à la chaîne qui sera présentée.  \(Les variables `userName` et `jobList` sont initialisées précédemment dans l'application.\)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#enumeratejobsinqueues)]
 [!code-csharp[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#enumeratejobsinqueues)]
 [!code-vb[DiagnoseProblematicPrintJob#EnumerateJobsInQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#enumeratejobsinqueues)]  
  
 L'exemple de code suivant reprend l'application de l'étape 2.  \(Voir ci\-dessus.\) Le travail problématique a été repéré et l'application demande les informations d'identification.  À partir de ces informations, elle crée les objets <xref:System.Printing.PrintServer>, <xref:System.Printing.PrintQueue> et <xref:System.Printing.PrintSystemJobInfo>.  
  
 À ce stade, l'application contient une structure de branche qui correspond aux deux façons de vérifier l'état d'un travail d'impression :  
  
-   Vous pouvez lire les indicateurs de la propriété <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A> qui est du type <xref:System.Printing.PrintJobStatus>.  
  
-   Vous pouvez lire chaque propriété appropriée telle que <xref:System.Printing.PrintSystemJobInfo.IsBlocked%2A> et <xref:System.Printing.PrintSystemJobInfo.IsInError%2A>.  
  
 Cet exemple illustrant les deux méthodes, l'utilisateur a été auparavant invité à choisir celle à utiliser et a répondu par l'affirmative s'il souhaitait opter pour les indicateurs de la propriété <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A>.  Voir ci\-dessous pour des informations détaillées sur les deux méthodes.  Enfin, l'application utilise une méthode appelée **ReportQueueAndJobAvailability** pour préciser si le travail peut être imprimé à ce moment de la journée.  Cette méthode est décrite dans [Déterminer si un travail d'impression peut être imprimé à cette heure de la journée](../../../../docs/framework/wpf/advanced/how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day.md).  
  
 [!code-cpp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#identifyanddiagnoseproblematicjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#identifyanddiagnoseproblematicjob)]
 [!code-vb[DiagnoseProblematicPrintJob#IdentifyAndDiagnoseProblematicJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#identifyanddiagnoseproblematicjob)]  
  
 Pour vérifier l'état du travail d'impression au moyen des indicateurs de la propriété <xref:System.Printing.PrintSystemJobInfo.JobStatus%2A>, vous contrôlez si chaque indicateur correspondant est défini.  La procédure standard pour vérifier si l'un des bits d'un ensemble de bits indicateurs est défini consiste à effectuer une opération AND logique en spécifiant l'ensemble d'indicateurs comme premier opérande et l'indicateur lui\-même comme deuxième opérande.  Comme l'indicateur lui\-même n'a qu'un seul bit défini, le résultat du AND logique est que, au plus, ce même bit est défini.  Pour déterminer si c'est le cas ou non, il suffit de comparer le résultat du AND logique à l'indicateur lui\-même.  Pour plus d'informations, consultez <xref:System.Printing.PrintJobStatus>, l'[&, opérateur \(référence C\#\)](../Topic/&%20Operator%20\(C%23%20Reference\).md) et <xref:System.FlagsAttribute>.  
  
 Pour chaque attribut dont le bit est défini, le code affiche cette information sur l'écran de la console et propose parfois une réponse possible.  \(La méthode **HandlePausedJob** qui est appelée si le travail ou la file d'attente sont suspendus est abordée ci\-dessous.\)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobattributes)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobattributes)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobAttributes](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobattributes)]  
  
 Pour vérifier l'état du travail d'impression à l'aide de propriétés individuelles, il vous suffit de lire chaque propriété et, si elle a la valeur `true`, d'afficher cette information sur l'écran de la console en proposant éventuellement une réponse possible.  \(La méthode **HandlePausedJob** qui est appelée si le travail ou la file d'attente sont suspendus est abordée ci\-dessous.\)  
  
 [!code-cpp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#spottroubleusingjobproperties)]
 [!code-csharp[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#spottroubleusingjobproperties)]
 [!code-vb[DiagnoseProblematicPrintJob#SpotTroubleUsingJobProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#spottroubleusingjobproperties)]  
  
 La méthode **HandlePausedJob** permet à l'utilisateur d'une application de reprendre à distance des travaux suspendus.  Comme la file d'attente à l'impression a peut\-être été suspendue pour de bonnes raisons, la méthode demande à l'utilisateur de confirmer sa décision de reprise.  En cas de réponse affirmative, la méthode <xref:System.Printing.PrintQueue.Resume%2A?displayProperty=fullName> est appelée.  
  
 L'utilisateur est ensuite invité à confirmer si le travail lui\-même doit reprendre, juste au cas où il ait été suspendu indépendamment de la file d'attente à l'impression.  Comparez <xref:System.Printing.PrintQueue.IsPaused%2A?displayProperty=fullName> et <xref:System.Printing.PrintSystemJobInfo.IsPaused%2A?displayProperty=fullName>. Si l'utilisateur répond par l'affirmative, <xref:System.Printing.PrintSystemJobInfo.Resume%2A?displayProperty=fullName> est appelée, sinon c'est <xref:System.Printing.PrintSystemJobInfo.Cancel%2A>.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#handlepausedjob)]
 [!code-csharp[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#handlepausedjob)]
 [!code-vb[DiagnoseProblematicPrintJob#HandlePausedJob](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#handlepausedjob)]  
  
## Voir aussi  
 <xref:System.Printing.PrintJobStatus>   
 <xref:System.Printing.PrintSystemJobInfo>   
 <xref:System.FlagsAttribute>   
 <xref:System.Printing.PrintQueue>   
 [&, opérateur \(référence C\#\)](../Topic/&%20Operator%20\(C%23%20Reference\).md)   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Vue d'ensemble de l'impression](../../../../docs/framework/wpf/advanced/printing-overview.md)