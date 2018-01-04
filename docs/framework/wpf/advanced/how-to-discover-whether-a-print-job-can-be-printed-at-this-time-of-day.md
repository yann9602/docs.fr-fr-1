---
title: "Comment : déterminer si un travail d'impression peut être imprimé à cette heure de la journée"
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
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ef9da205792823b7069024c5e4a3e9ac80d60a24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>Comment : déterminer si un travail d'impression peut être imprimé à cette heure de la journée
Les files d’attente d’impression ne sont pas toujours disponibles pour 24 heures par jour. Ils ont des propriétés au moment du début et de fin qui peuvent être définies pour les rendre indisponibles à certains moments de la journée. Cette fonctionnalité peut être utilisée, par exemple, pour réserver une imprimante à l’usage exclusif d’un département après 17 h 00. Ce service aurait une autre file d’attente l’imprimante que les autres services à utiliser. La file d’attente pour les autres services a la valeur n’est pas disponible après 17 h 00, alors que la file d’attente pour le département privilégié peut être définie pour être disponible à tout moment.  
  
 En outre, les travaux d’impression eux-mêmes peuvent être définis pour être imprimables uniquement dans un intervalle de temps spécifié.  
  
 Le <xref:System.Printing.PrintQueue> et <xref:System.Printing.PrintSystemJobInfo> classes exposées dans le [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] de [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)] fournissent un moyen de vérifier à distance si un travail d’impression donné peut imprimer sur une file d’attente donnée à l’heure actuelle.  
  
## <a name="example"></a>Exemple  
 L’exemple ci-dessous est un exemple qui peut diagnostiquer les problèmes liés à un travail d’impression.  
  
 Il existe deux principales étapes de ce type de fonction comme suit.  
  
1.  Lecture la <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> et <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriétés de la <xref:System.Printing.PrintQueue> pour déterminer si l’heure actuelle est entre eux.  
  
2.  Lecture la <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> et <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> propriétés de la <xref:System.Printing.PrintSystemJobInfo> pour déterminer si l’heure actuelle est entre eux.  
  
 Mais les complications provient du fait que ces propriétés ne sont pas <xref:System.DateTime> objets. Au lieu de cela, ils sont <xref:System.Int32> objets qui expriment l’heure du jour en tant que le nombre de minutes depuis minuit. En outre, il n’est pas minuit dans le fuseau horaire actuel, mais minuit UTC (Coordinated Universal Time).  
  
 Le premier exemple de code présente la méthode statique **ReportQueueAndJobAvailability**, qui est passé un <xref:System.Printing.PrintSystemJobInfo> et appelle les méthodes d’assistance pour déterminer si le travail peut être imprimé à l’heure actuelle et, si, quand il peut s’impriment pas. Notez qu’un <xref:System.Printing.PrintQueue> n’est pas passé à la méthode. C’est parce que le <xref:System.Printing.PrintSystemJobInfo> inclut une référence à la file d’attente dans son <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> propriété.  
  
 Les méthodes subordonnées incluent surchargées **ReportAvailabilityAtThisTime** méthode qui peut également accepter soit un <xref:System.Printing.PrintQueue> ou un <xref:System.Printing.PrintSystemJobInfo> en tant que paramètre. Il existe également un **TimeConverter.ConvertToLocalHumanReadableTime**. Toutes ces méthodes sont décrites ci-dessous.  
  
 Le **ReportQueueAndJobAvailability** méthode commence par vérifier si la file d’attente ou le travail d’impression n’est pas disponible pour l’instant. Si un d’eux n’est pas disponible, il vérifie ensuite si la file d’attente est indisponible. S’il n’est pas disponible, la méthode signale ce fait et l’heure lorsque la file d’attente est disponible. Il vérifie ensuite le travail et si elle n’est pas disponible, il signale le prochain intervalle pendant qu’elle peut imprimer. Enfin, la méthode signale la première heure lorsque le travail peut être imprimé. Ceci est la plus récente de deux fois de suite.  
  
-   L’heure auxquelles la file d’attente d’impression est ensuite disponible.  
  
-   L’heure auxquelles le travail d’impression est ensuite disponible.  
  
 Lors du signalement des heures de la journée, le <xref:System.DateTime.ToShortTimeString%2A> méthode est également appelée car la méthode supprime les années, mois et jours de la sortie. Vous ne pouvez pas restreindre la disponibilité d’une file d’attente d’impression ou d’un travail d’impression pour les jours, mois ou années particuliers.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 Les deux surcharges de la **ReportAvailabilityAtThisTime** méthode sont identiques à l’exception du type passé les uns aux autres, ainsi que la <xref:System.Printing.PrintQueue> version est présentée ci-dessous.  
  
> [!NOTE]
>  Le fait que les méthodes sont identiques à l’exception de type déclenche la question de savoir pourquoi l’exemple ne crée pas une méthode générique **ReportAvailabilityAtThisTime\<T >**. La raison est qu’une telle méthode devrait être limité à une classe qui a le **StartTimeOfDay** et **UntilTimeOfDay** propriétés de la méthode appelle, mais une méthode générique peut uniquement être limité à un une seule classe et la seule classe commune aux deux <xref:System.Printing.PrintQueue> et <xref:System.Printing.PrintSystemJobInfo> l’héritage arborescence est <xref:System.Printing.PrintSystemObject> n’ayant pas de telles propriétés.  
  
 Le **ReportAvailabilityAtThisTime** (méthode) (présentée dans l’exemple de code ci-dessous) commence par initialiser un <xref:System.Boolean> variable sentinelle `true`. Elle sera réinitialisée à `false`, si la file d’attente n’est pas disponible.  
  
 Ensuite, la méthode vérifie si le début et « jusqu'à ce que « heures sont identiques. Dans le cas, la file d’attente est toujours disponible, alors la méthode retourne `true`.  
  
 Si la file d’attente n’est pas disponible tout le temps, la méthode utilise la méthode statique <xref:System.DateTime.UtcNow%2A> propriété à obtenir l’heure actuelle en tant qu’un <xref:System.DateTime> objet. (Nous n’avez pas besoin de heure locale, car le <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> et <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> propriétés sont elles-mêmes en heure UTC.)  
  
 Toutefois, ces deux propriétés ne sont pas <xref:System.DateTime> objets. Ils sont <xref:System.Int32>s exprimant le temps que le nombre de minutes après minuit UTC. Donc nous devons convertir notre <xref:System.DateTime> objet en minutes après minuit. Lorsque que vous avez terminé, la méthode vérifie simplement pour voir si « maintenant » est entre le début de la file d’attente et « jusqu'à ce que « heures, définit la sentinelle False si « maintenant » n’est pas entre les deux heures et retourne la sentinelle.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 Le **TimeConverter.ConvertToLocalHumanReadableTime** (méthode) (présentée dans l’exemple de code ci-dessous) n’utilise pas les méthodes introduites avec [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], de sorte que la description est brève. La méthode a une double tâche de conversion : il doit prendre un entier exprimant des minutes après minuit et le convertir en une heure contrôlable de visu et il doit le convertir en heure locale. Il y parvient en créant d’abord un <xref:System.DateTime> objet qui est définie à minuit UTC, puis il utilise le <xref:System.DateTime.AddMinutes%2A> méthode pour ajouter les minutes qui ont été passés à la méthode. Cela retourne une nouvelle <xref:System.DateTime> exprimant l’heure d’origine qui a été passé à la méthode. Le <xref:System.DateTime.ToLocalTime%2A> méthode convertit ensuite cette valeur d’heure locale.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.DateTime>  
 <xref:System.Printing.PrintSystemJobInfo>  
 <xref:System.Printing.PrintQueue>  
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Vue d’ensemble de l’impression](../../../../docs/framework/wpf/advanced/printing-overview.md)
