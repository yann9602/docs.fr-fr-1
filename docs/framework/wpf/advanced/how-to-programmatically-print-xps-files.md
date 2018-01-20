---
title: "Comment : imprimer des fichiers XPS par programmation"
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
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b58e617fb04ecaba45ed655dc650459e89453dd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-programmatically-print-xps-files"></a>Comment : imprimer des fichiers XPS par programmation
Vous pouvez utiliser une surcharge de la <xref:System.Printing.PrintQueue.AddJob%2A> méthode pour imprimer [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] fichiers sans ouvrir une <xref:System.Windows.Controls.PrintDialog> ou, en principe, n’importe quel [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] du tout.  
  
 Vous pouvez également imprimer [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] à l’aide de la plupart des fichiers <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> et <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> méthodes de la <xref:System.Windows.Xps.XpsDocumentWriter>. Pour en savoir plus sur ce sujet, consultez l’article [Printing an XPS Document](http://msdn.microsoft.com/library/849555c8-0c4e-48c0-86bc-a5494c69b36c) (Impression d’un document XPS).  
  
 Une autre façon d’impression [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] consiste à utiliser le <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> ou <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> méthodes de la <xref:System.Windows.Controls.PrintDialog> contrôle. Consultez l’article [Appeler une boîte de dialogue Imprimer](../../../../docs/framework/wpf/advanced/how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Exemple  
 Les étapes principales à l’aide du paramètre de trois <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> méthode sont les suivantes. L’exemple ci-dessous donne des détails.  
  
1.  Déterminez si l’imprimante est une imprimante XPSDrv. (Voir [Vue d’ensemble de l’impression](../../../../docs/framework/wpf/advanced/printing-overview.md) pour plus d’informations sur XPSDrv.)  
  
2.  Si l’imprimante n’est pas une imprimante XPSDrv, définissez l’état de cloisonnement du thread sur Thread unique.  
  
3.  Instanciez un serveur d’impression et un objet de file d’attente à l’impression.  
  
4.  Appelez la méthode, en spécifiant un nom de tâche, le fichier à imprimer et un <xref:System.Boolean> indicateur qui spécifie si l’imprimante est une imprimante ou non.  
  
 L’exemple ci-dessous montre comment imprimer par lot tous les fichiers [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] d’un répertoire. Bien que l’application invite l’utilisateur de spécifier le répertoire, les trois paramètres <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> méthode ne requiert pas un [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Elle peut être utilisée dans n’importe quel chemin d’accès de code où vous disposez d’un nom de fichier [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] et d’un chemin que vous pouvez lui transmettre.  
  
 Les trois paramètres <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> surcharge de <xref:System.Printing.PrintQueue.AddJob%2A> doivent s’exécuter dans un cloisonnement du thread unique à chaque fois que le <xref:System.Boolean> paramètre est `false`, qui doit être quand une imprimante est utilisée. Toutefois, l’état de cloisonnement par défaut pour [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] est multithread. Cette valeur par défaut doit être modifiée puisque l’exemple utilise une imprimante non-XPSDrv.  
  
 Il existe deux moyens de modifier la valeur par défaut. Consiste simplement à ajouter le <xref:System.STAThreadAttribute> (autrement dit, «`[System.STAThreadAttribute()]`») juste au-dessus de la première ligne de l’application `Main` (méthode) (généralement «`static void Main(string[] args)`»). Toutefois, de nombreuses applications nécessitent que le `Main` méthode peuvent avoir un état de cloisonnement multithread, il est une deuxième méthode : placez l’appel à <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> dans un thread séparé dont l’état de cloisonnement est défini à <xref:System.Threading.ApartmentState.STA> avec <xref:System.Threading.Thread.SetApartmentState%2A>. L’exemple suivant utilise cette deuxième technique.  
  
 En conséquence, l’exemple commence en instanciant un <xref:System.Threading.Thread> objet et en lui passant un **PrintXPS** méthode comme étant le <xref:System.Threading.ThreadStart> paramètre. (La méthode **PrintXPS** est expliquée plus loin dans l’exemple.) Ensuite, le thread est défini sur un thread unique cloisonné. Le seul code restant de la méthode `Main` démarre le nouveau thread.  
  
 L’exemple se base principalement sur la méthode `static`**BatchXPSPrinter.PrintXPS**. Une fois que le serveur d’impression et la file d’attente ont été créés, la méthode invite l’utilisateur à spécifier un répertoire contenant les fichiers [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]. Après avoir vérifié que le répertoire existe bien et qu’il contient les fichiers *.xps, la méthode ajoute chacun de ces fichiers à la file d’attente à l’impression. L’exemple suppose que l’imprimante est non XPSDrv, donc nous passons `false` au dernier paramètre de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> (méthode). Pour cette raison, la méthode validera le balisage [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dans le fichier avant d’essayer de le convertir en langage de description de page de l’imprimante. Si la validation échoue, une exception est générée. L’exemple de code interceptera l’exception, en informera l’utilisateur et passera ensuite au fichier [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] suivant.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 Si vous utilisez une imprimante XPSDrv, vous pouvez définir le paramètre final sur `true`. Dans ce cas, puisque [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] est le langage de description de page de l’imprimante, la méthode enverra le fichier à l’imprimante sans le valider ou le convertir dans un autre langage de description de page. Si vous n’êtes pas certain, au moment du design de l’application utilise une imprimante, vous pouvez modifier l’application pour qu’elle lise le <xref:System.Printing.PrintQueue.IsXpsDevice%2A> propriété et la branche en fonction de ce qu’il trouve.  
  
 Dans la mesure où peu d’imprimantes XPSDrv seront disponibles immédiatement après la publication de [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] et [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], vous devrez peut-être déguiser une imprimante non-XPSDrv en imprimante XPSDrv. Pour ce faire, ajoutez le fichier Pipelineconfig.xml à la liste des fichiers dans la clé de Registre suivante de l’ordinateur qui exécute votre application :  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\*\<PseudoXPSPrinter>*\DependentFiles  
  
 où *\<PseudoXPSPrinter>* est une file d’attente à l’impression. L’ordinateur doit ensuite être redémarré.  
  
 Cette déguisé vous permettra de passer `true` comme dernier paramètre de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> sans provoquer une exception, mais puisque  *\<PseudoXPSPrinter >* n’est pas réellement une imprimante, seront imprimées.  
  
 **Remarque** Pour plus de simplicité, l’exemple ci-dessus utilise une extension *.xps pour spécifier qu’un fichier est [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]. Toutefois, les fichiers [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] n’ont pas obligatoirement cette extension. L’outil [isXPS.exe (isXPS Conformance Tool)](http://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3) permet de tester la conformité d’un fichier aux normes [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.AddJob%2A>  
 <xref:System.Threading.ApartmentState>  
 <xref:System.STAThreadAttribute>  
 [XPS](http://www.microsoft.com/xps)  
 [Impression d’un Document XPS](http://msdn.microsoft.com/library/849555c8-0c4e-48c0-86bc-a5494c69b36c)  
 [Threading managé et non managé](http://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5)  
 [isXPS.exe (isXPS Conformance Tool)](http://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3)  
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Vue d’ensemble de l’impression](../../../../docs/framework/wpf/advanced/printing-overview.md)
