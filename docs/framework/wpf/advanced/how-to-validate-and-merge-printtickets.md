---
title: "Comment&#160;: valider et fusionner des PrintTicket | Microsoft Docs"
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
  - "fusionner des PrintTicket"
  - "PrintTicket, fusionner"
  - "PrintTicket, validation"
  - "validation de PrintTicket"
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: valider et fusionner des PrintTicket
Le [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Schéma d'impression \(page éventuellement en anglais](http://go.microsoft.com/fwlink/?LinkId=186397) comprend les éléments <xref:System.Printing.PrintCapabilities> et <xref:System.Printing.PrintTicket> flexibles et extensibles.  Le premier comptabilise les fonctions d'un périphérique d'impression et le dernier spécifie comment le périphérique doit utiliser ces fonctions en ce qui concerne une séquence particulière de documents, de document individuel ou de page individuelle.  
  
 Une séquence type de tâches pour une application prenant en charge l'impression serait comme suit.  
  
1.  Déterminer les fonctions d'une imprimante.  
  
2.  Configurer un <xref:System.Printing.PrintTicket> pour utiliser ces fonctions.  
  
3.  Valider le <xref:System.Printing.PrintTicket>.  
  
 Cet article indique comment faire.  
  
## Exemple  
 Dans l'exemple simple ci\-dessous, nous nous intéressons uniquement à savoir si une imprimante peut prendre en charge l'impression recto\-verso.  Les étapes principales sont les suivantes.  
  
1.  Récupérer un objet <xref:System.Printing.PrintCapabilities> avec la méthode <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>.  
  
2.  Testez la présence de la fonction que vous souhaitez.  Dans l'exemple ci\-dessous, nous testons la propriété <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> de l'objet <xref:System.Printing.PrintCapabilities> pour la présence de la fonction d'impression recto verso avec la « rotation de page » le long du long côté de la feuille.  Puisque <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> est une collection, nous utilisons la méthode `Contains` de <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
    > [!NOTE]
    >  Cette étape n'est pas strictement nécessaire.  La méthode <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> utilisée ci\-dessous vérifiera chaque demande dans le <xref:System.Printing.PrintTicket> par rapport aux fonctions de l'imprimante.  Si la fonction demandée n'est pas prise en charge par l'imprimante, le pilote d'imprimante substituera une autre demande dans le <xref:System.Printing.PrintTicket> retourné par la méthode.  
  
3.  Si l'imprimante prend en charge l'impression recto verso, l'exemple de code crée un <xref:System.Printing.PrintTicket> qui demande la copie recto verso.  Mais l'application ne spécifie pas chaque paramètre de l'imprimante possible disponible dans l'élément <xref:System.Printing.PrintTicket>.  Ce serait à la fois une perte de temps pour le programmeur et pour le programme.  À la place, le codes définit uniquement la demande d'impression recto verso puis fusionne ce <xref:System.Printing.PrintTicket> avec un <xref:System.Printing.PrintTicket> existant, entièrement configuré et validé, qui dans ce cas est le <xref:System.Printing.PrintTicket> par défaut de l'utilisateur.  
  
4.  En conséquence, l'exemple appelle la méthode <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> pour fusionner le nouveau, minime <xref:System.Printing.PrintTicket> avec le <xref:System.Printing.PrintTicket> par défaut de l'utilisateur.  Un <xref:System.Printing.ValidationResult> est retourné comportant le nouveau <xref:System.Printing.PrintTicket> comme l'une de ses propriétés.  
  
5.  L'exemple teste ensuite le nouveau <xref:System.Printing.PrintTicket> pour savoir s'il demande l'impression recto verso.  Si c'est le cas, l'exemple le déclare alors comme le nouveau ticket d'impression par défaut pour l'utilisateur.  Si l'étape 2 ci\-dessus avait été ignorée et que l'imprimante ne prenait pas en charge l'impression recto verso le long du long côté, le test aurait renvoyé la valeur `false`.  \(Voir la remarque ci\-dessus\).  
  
6.  La dernière étape importante est de valider la modification à la propriété <xref:System.Printing.PrintQueue.UserPrintTicket%2A> du <xref:System.Printing.PrintQueue> avec la méthode <xref:System.Printing.PrintQueue.Commit%2A>.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Afin que vous puissiez tester cet exemple rapidement, le reste est présenté ci\-dessous.  Créez un projet et un espace de noms, puis collez les deux extraits de code de cet article dans le bloc d'espace de noms.  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## Voir aussi  
 <xref:System.Printing.PrintCapabilities>   
 <xref:System.Printing.PrintTicket>   
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>   
 <xref:System.Printing.PrintServer>   
 <xref:System.Printing.EnumeratedPrintQueueTypes>   
 <xref:System.Printing.PrintQueue>   
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Vue d'ensemble de l'impression](../../../../docs/framework/wpf/advanced/printing-overview.md)   
 [Schéma d'impression \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=186397)