---
title: "Comment&#160;: d&#233;terminer si un travail d&#39;impression peut &#234;tre imprim&#233; &#224; cette heure de la journ&#233;e | Microsoft Docs"
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
  - "travaux d'impression, minutage"
  - "files d'attente à l'impression, minutage"
  - "imprimantes, disponibilité"
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: d&#233;terminer si un travail d&#39;impression peut &#234;tre imprim&#233; &#224; cette heure de la journ&#233;e
Les files d'attente à l'impression ne sont pas toujours disponibles 24 heures sur 24.  Elles ont des propriétés d'heures de début et de fin qui peuvent être définies pour les rendre non disponibles à certaines heures de la journée.  Cette fonctionnalité peut être utilisée, par exemple, pour réserver une imprimante en vue de l'utilisation exclusive d'un département après 17 heures.  Ce département aurait pour les services de l'imprimante une file d'attente différente de celle des autres départements.  La file d'attente pour les autres départements serait définie comme étant non disponible après 17 heures, alors que pour le département privilégié la file d'attente serait définie pour être disponible tout le temps.  
  
 De plus, les travaux d'impression eux\-mêmes seraient définis pour être imprimables uniquement pendant un intervalle de temps spécifié.  
  
 Les classes <xref:System.Printing.PrintQueue> et <xref:System.Printing.PrintSystemJobInfo> exposées dans les [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] de [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] offrent le moyen de vérifier à distance si un travail d'impression donné peut être imprimé sur une file d'attente spécifique à l'heure actuelle.  
  
## Exemple  
 L'exemple suivant est un exemple qui peut diagnostiquer des problèmes concernant un travail d'impression.  
  
 Il existe deux étapes majeures pour ce genre de fonction, comme suit.  
  
1.  Lisez les propriétés <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> et <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> de la <xref:System.Printing.PrintQueue> pour déterminer si l'heure actuelle se situe entre les deux.  
  
2.  Lisez les propriétés <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> et <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> de la <xref:System.Printing.PrintSystemJobInfo> pour déterminer si l'heure actuelle se situe entre les deux.  
  
 Mais les complications naissent du fait que ces propriétés ne sont pas des objets <xref:System.DateTime>.  Ce sont plutôt des objets <xref:System.Int32> qui expriment l'heure du jour en tant que nombre de minutes depuis minuit.  De plus, il ne s'agit pas de minuit dans le fuseau actuel, mais minuit en temps UTC \(Coordinated Universal Time\).  
  
 Le premier exemple de code présente la méthode statique **ReportQueueAndJobAvailability**, qui reçoit une <xref:System.Printing.PrintSystemJobInfo> et appelle les méthodes d'assistance afin de déterminer si le travail peut être imprimé à l'heure actuelle et, sinon, à quelle heure il peut être imprimé.  Notez qu'une <xref:System.Printing.PrintQueue> n'est pas passée à la méthode.  Cela tient au fait que <xref:System.Printing.PrintSystemJobInfo> inclut une référence vers la file d'attente dans sa propriété <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A>.  
  
 Les méthodes subordonnées incluent la méthode **ReportAvailabilityAtThisTime** surchargée qui peut prendre <xref:System.Printing.PrintQueue> ou <xref:System.Printing.PrintSystemJobInfo> en tant que paramètre.  Il y a aussi une **TimeConverter.ConvertToLocalHumanReadableTime**.  Toutes ces méthodes sont passées en revue ci\-dessous.  
  
 La méthode **ReportQueueAndJobAvailability** commence par vérifier si la file d'attente ou le travail d'impression n'est pas disponible à cette heure.  Si l'un des deux n'est pas disponible, elle vérifie alors si la file d'attente n'est pas disponible.  Si elle n'est pas disponible, alors la méthode signale ce fait et l'heure à laquelle la file d'attente redeviendra disponible.  Elle vérifie ensuite le travail et si celui\-ci n'est pas disponible, elle signale le prochain intervalle pendant lequel elle pourra imprimer.  Enfin, la méthode signale la première heure à laquelle le travail pourra être imprimé.  Il s'agit de l'heure la plus tardive des deux suivantes.  
  
-   L'heure à laquelle la file d'attente à l'impression sera disponible la prochaine fois.  
  
-   L'heure à laquelle le travail d'impression sera disponible la prochaine fois.  
  
 Lors de l'indication des heures de la journée, la méthode <xref:System.DateTime.ToShortTimeString%2A> est également appelée car la méthode supprime les heures, les mois et les jours de la sortie.  Vous ne pouvez pas restreindre la disponibilité de la file d'attente ou d'un travail d'impression en fonction d'années, de mois ou de jours particuliers.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 Les deux surcharges de la méthode **ReportAvailabilityAtThisTime** sont identiques sauf pour le type qui leur est passé, ce qui fait que seule la version <xref:System.Printing.PrintQueue> est présentée ci\-dessous.  
  
> [!NOTE]
>  Le fait que les méthodes soient identiques sauf pour le type soulève la question de savoir pourquoi l'exemple ne crée pas une méthode générique **ReportAvailabilityAtThisTime\<T\>**.  La raison est qu'il aurait fallu restreindre une telle méthode à une classe qui a les propriétés **StartTimeOfDay** et **UntilTimeOfDay** que la méthode appelle, mais une méthode générique peut seulement être restreinte à une seule classe et la seule classe commune aux deux <xref:System.Printing.PrintQueue> et <xref:System.Printing.PrintSystemJobInfo> est l'arborescence d'héritage <xref:System.Printing.PrintSystemObject> qui ne possède pas de telles propriétés.  
  
 La méthode **ReportAvailabilityAtThisTime** \(présentée dans l'exemple de code ci\-dessous\) commence par initialiser une variable sentinelle <xref:System.Boolean> à `true`.  Elle sera réinitialisée à `false`, si la file d'attente n'est pas disponible.  
  
 Ensuite, la méthode vérifie si les heures de début et « jusqu'à » sont identiques.  Si c'est le cas, la file d'attente est toujours disponible, alors la méthode retourne `true`.  
  
 Si la file d'attente est non disponible tout le temps, la méthode utilise la propriété <xref:System.DateTime.UtcNow%2A> statique pour obtenir l'heure actuelle en tant qu'objet <xref:System.DateTime>.  \(Nous n'avons pas besoin de l'heure locale car les propriétés <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> et <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> sont elles\-mêmes en heure UTC.\)  
  
 Cependant, ces deux propriétés ne sont pas des objets <xref:System.DateTime>.  Il s'agit de <xref:System.Int32>s qui expriment l'heure en tant que nombre de minutes après UTC et minuit.  Nous devons donc convertir notre objet <xref:System.DateTime> en minutes après minuit.  Une fois cela fait, la méthode vérifie simplement si « maintenant » se situe entre les heures de début et « jusqu'à » de la file d'attente, affecte à la sentinelle la valeur False si « maintenant » ne se situe pas entre les deux heures, et retourne la sentinelle.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 La méthode **TimeConverter.ConvertToLocalHumanReadableTime** \(présentée dans l'exemple de code ci\-dessous\) n'utilise aucune méthode introduite avec [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], ce qui fait que la description est brève.  La méthode a une double tâche de conversion : elle doit prendre un entier exprimant des minutes après minuit et le convertir en heure explicite, puis convertir cette valeur en heure locale.  Pour ce faire, elle crée d'abord un objet <xref:System.DateTime> qui a la valeur UTC minuit, puis utilise la méthode <xref:System.DateTime.AddMinutes%2A> pour ajouter les minutes passées à la méthode.  Cela retourne une nouvelle <xref:System.DateTime> exprimant l'heure d'origine passée à la méthode.  La méthode <xref:System.DateTime.ToLocalTime%2A> convertit ensuite cette valeur en heure locale.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## Voir aussi  
 <xref:System.DateTime>   
 <xref:System.Printing.PrintSystemJobInfo>   
 <xref:System.Printing.PrintQueue>   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Vue d'ensemble de l'impression](../../../../docs/framework/wpf/advanced/printing-overview.md)