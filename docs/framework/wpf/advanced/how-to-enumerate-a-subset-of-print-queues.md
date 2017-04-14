---
title: "Comment&#160;: &#233;num&#233;rer un sous-ensemble de files d&#39;attente &#224; l&#39;impression | Microsoft Docs"
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
  - "énumérer, sous-ensemble de files d'attente à l'impression"
  - "files d'attente à l'impression, énumérer un sous-ensemble de"
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: &#233;num&#233;rer un sous-ensemble de files d&#39;attente &#224; l&#39;impression
Les professionnels de l'informatique qui gèrent des parcs d'imprimantes à l'échelle de l'entreprise sont souvent amenés à générer une liste des imprimantes dotées de certaines caractéristiques.  Cette fonctionnalité est fournie par la méthode <xref:System.Printing.PrintServer.GetPrintQueues%2A> d'un objet <xref:System.Printing.PrintServer> et l'énumération <xref:System.Printing.EnumeratedPrintQueueTypes>.  
  
## Exemple  
 Dans l'exemple suivant, le code commence par créer un tableau d'indicateurs qui spécifient les caractéristiques des files d'attente à l'impression à répertorier.  Dans cet exemple, nous recherchons les files d'attente à l'impression qui sont installées localement sur le serveur d'impression et partagées.  L'énumération <xref:System.Printing.EnumeratedPrintQueueTypes> offre de nombreuses autres possibilités.  
  
 Le code crée ensuite un objet <xref:System.Printing.LocalPrintServer>, une classe dérivée de <xref:System.Printing.PrintServer>.  Le serveur d'impression local est l'ordinateur sur lequel s'exécute l'application.  
  
 La dernière étape importante consiste à passer le tableau à la méthode <xref:System.Printing.PrintServer.GetPrintQueues%2A>.  
  
 Enfin, les résultats sont présentés à l'utilisateur.  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 Vous pouvez étendre cet exemple en faisant en sorte que la boucle `foreach` qui parcourt chaque file d'attente à l'impression effectue un filtrage supplémentaire.  Par exemple, vous pourriez filtrer les imprimantes qui ne prennent pas en charge l'impression recto\-verso en demandant à la boucle d'appeler la méthode <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> de chaque file d'attente à l'impression et de vérifier si la valeur retournée indique la présence de l'impression recto\-verso.  
  
## Voir aussi  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>   
 <xref:System.Printing.PrintServer>   
 <xref:System.Printing.LocalPrintServer>   
 <xref:System.Printing.EnumeratedPrintQueueTypes>   
 <xref:System.Printing.PrintQueue>   
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Vue d'ensemble de l'impression](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [Microsoft XPS Document Writer \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=147319)