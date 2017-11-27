---
title: "Comment : énumérer un sous-ensemble de files d'attente à l'impression"
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
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 393d1692526551b1eb9aa16f48d3c78c3cd6692f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>Comment : énumérer un sous-ensemble de files d'attente à l'impression
Une situation courante rencontrée par les professionnels informatiques (IT) de la gestion d’un ensemble d’échelle de la société d’imprimantes est pour générer une liste des imprimantes présentant certaines caractéristiques. Cette fonctionnalité est fournie par le <xref:System.Printing.PrintServer.GetPrintQueues%2A> méthode d’un <xref:System.Printing.PrintServer> objet et le <xref:System.Printing.EnumeratedPrintQueueTypes> énumération.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple ci-dessous, le code commence par créer un tableau d’indicateurs qui spécifient les caractéristiques des files d’attente, que nous souhaitons liste. Dans cet exemple, nous recherchons les files d’attente qui sont installées localement sur le serveur d’impression et sont partagés. Le <xref:System.Printing.EnumeratedPrintQueueTypes> énumération offre de nombreuses autres possibilités.  
  
 Le code crée ensuite un <xref:System.Printing.LocalPrintServer> de l’objet, une classe dérivée de <xref:System.Printing.PrintServer>. Le serveur d’impression local est l’ordinateur sur lequel l’application est en cours d’exécution.  
  
 La dernière étape importante consiste à passer le tableau à la <xref:System.Printing.PrintServer.GetPrintQueues%2A> (méthode).  
  
 Enfin, les résultats sont présentés à l’utilisateur.  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 Vous pouvez étendre cet exemple en ayant la `foreach` boucle parcourt chaque file d’attente d’impression faire davantage de filtrage. Par exemple, vous pourriez filtrer les imprimantes qui ne gèrent pas l’impression recto-verso en demandant à l’appel de la boucle chaque file d’attente à l’impression <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> (méthode) et test, la valeur retournée pour la présence de duplex.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Vue d’ensemble de l’impression](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319)
