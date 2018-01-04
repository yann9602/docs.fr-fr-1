---
title: "Comment : valider et fusionner des PrintTicket"
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
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5cf2091d50433bb936b3d4976d1c3eabea73edc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-validate-and-merge-printtickets"></a>Comment : valider et fusionner des PrintTicket
Le [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [schéma d’impression](http://go.microsoft.com/fwlink/?LinkId=186397) inclut flexible et extensible <xref:System.Printing.PrintCapabilities> et <xref:System.Printing.PrintTicket> éléments. Le premier comptabilise les fonctions d’un périphérique d’impression et le dernier spécifie comment l’appareil doit utiliser ces fonctionnalités par rapport à une séquence particulière de documents, de document individuel ou de page individuelle.  
  
 Une séquence standard de tâches pour une application qui prend en charge l’impression serait comme suit.  
  
1.  Déterminer les fonctionnalités d’une imprimante.  
  
2.  Configurer un <xref:System.Printing.PrintTicket> pour utiliser ces fonctions.  
  
3.  Valider la <xref:System.Printing.PrintTicket>.  
  
 Cet article explique comment effectuer cette opération.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple ci-dessous, nous sommes intéressés uniquement si une imprimante peut prendre en charge : impression recto-verso. Les étapes principales sont les suivantes.  
  
1.  Obtenir un <xref:System.Printing.PrintCapabilities> de l’objet avec le <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> (méthode).  
  
2.  Tester la présence de la fonctionnalité souhaitée. Dans l’exemple ci-dessous, nous testons la <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> propriété de la <xref:System.Printing.PrintCapabilities> la présence de la fonction d’impression sur les deux côtés d’une feuille de papier, la rotation de « page » de l’objet le long du côté long de la feuille. Étant donné que <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> est une collection, nous utilisons le `Contains` méthode <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
    > [!NOTE]
    >  Cette étape n’est pas strictement nécessaire. Le <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> méthode utilisée ci-dessous vérifiera chaque demande le <xref:System.Printing.PrintTicket> aux capacités de l’imprimante. Si la fonction demandée n’est pas pris en charge par l’imprimante, le pilote d’imprimante substituera une autre demande dans le <xref:System.Printing.PrintTicket> retourné par la méthode.  
  
3.  Si l’imprimante prend en charge l’impression recto verso, l’exemple de code crée un <xref:System.Printing.PrintTicket> qui demande la duplication. Mais l’application ne spécifie pas de chaque paramètre disponible dans l’imprimante possible la <xref:System.Printing.PrintTicket> élément. Ce serait une perte de programmeur et durée du programme. Au lieu de cela, le code définit uniquement la demande d’impression recto verso et puis fusionne ce <xref:System.Printing.PrintTicket> avec un existant, entièrement configuré et validé, <xref:System.Printing.PrintTicket>, dans ce cas, par défaut de l’utilisateur <xref:System.Printing.PrintTicket>.  
  
4.  En conséquence, l’exemple appelle la <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> à fusionner la nouvelle méthode minimal, <xref:System.Printing.PrintTicket> avec la valeur par défaut de l’utilisateur <xref:System.Printing.PrintTicket>. Cette opération retourne un <xref:System.Printing.ValidationResult> qui inclut la nouvelle <xref:System.Printing.PrintTicket> comme l’un de ses propriétés.  
  
5.  L’exemple vérifie ensuite que la nouvelle <xref:System.Printing.PrintTicket> recto verso des demandes. Dans ce cas, l’exemple met à nouveau ticket d’impression par défaut pour l’utilisateur. Si l’étape 2 ci-dessus avait été ignorée et l’imprimante ne prenait pas en charge recto verso le long du côté long, puis aurait pour résultat le test `false`. (Voir la Remarque ci-dessus.)  
  
6.  La dernière étape importante consiste à valider la modification à la <xref:System.Printing.PrintQueue.UserPrintTicket%2A> propriété de la <xref:System.Printing.PrintQueue> avec la <xref:System.Printing.PrintQueue.Commit%2A> (méthode).  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Afin que vous pouvez rapidement tester cet exemple, le reste est présenté ci-dessous. Créez un projet et un espace de noms, puis collez les deux extraits de code dans cet article dans le bloc d’espace de noms.  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Vue d’ensemble de l’impression](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Schéma d’impression](http://go.microsoft.com/fwlink/?LinkId=186397)
