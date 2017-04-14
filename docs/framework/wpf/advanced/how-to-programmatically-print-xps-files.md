---
title: "Comment&#160;: imprimer des fichiers XPS par programmation | Microsoft Docs"
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
  - "imprimer des fichiers XPS par programmation"
  - "fichiers XPS, imprimer par programmation"
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: imprimer des fichiers XPS par programmation
Vous pouvez utiliser une surcharge de la méthode <xref:System.Printing.PrintQueue.AddJob%2A> pour imprimer des fichiers [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] sans ouvrir de <xref:System.Windows.Controls.PrintDialog> ni, en principe, aucune [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  
  
 Vous pouvez également imprimer des fichiers [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] à l'aide des nombreuses méthodes <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> et <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> du <xref:System.Windows.Xps.XpsDocumentWriter>.  Pour plus d'informations à ce sujet, [Printing an XPS Document](http://msdn.microsoft.com/fr-fr/849555c8-0c4e-48c0-86bc-a5494c69b36c).  
  
 Une autre façon d'imprimer du [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] est d'utiliser les méthodes<xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> ou <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> du contrôle <xref:System.Windows.Controls.PrintDialog>.  Consultez [Appeler une boîte de dialogue Imprimer](../../../../docs/framework/wpf/advanced/how-to-invoke-a-print-dialog.md).  
  
## Exemple  
 Les étapes principales à l'utilisation de la méthode des trois paramètres <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> sont les suivantes.  L'exemple ci\-dessous apporte des détails à ce sujet.  
  
1.  Déterminez si l'imprimante est une imprimante XPSDrv.  \(Consultez [Vue d'ensemble de l'impression](../../../../docs/framework/wpf/advanced/printing-overview.md) pour plus d'informations sur XPSDrv.\)  
  
2.  Si l'imprimante n'est pas une imprimante XPSDrv, affectez STA \(Single Thread Apartment\) à l'état de cloisonnement du thread.  
  
3.  Instanciez un serveur d'impression et un objet de la file d'attente à l'impression.  
  
4.  Appelez la méthode, en spécifiant le nom du travail, le fichier à imprimer et un indicateur <xref:System.Boolean> qui signale si l'imprimante est une imprimante XPSDrv ou pas.  
  
 L'exemple suivant montre comment imprimer par lots tous les fichiers [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dans un répertoire.  Bien que l'application invite l'utilisateur à spécifier le répertoire, la méthode des trois paramètres <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> ne requiert pas d'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].  Elle peut être utilisée dans un chemin d'accès au code dans lequel vous avez un nom de fichier [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] et un chemin d'accès que vous pouvez passer à celui\-ci.  
  
 La surcharge des trois paramètres <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> de <xref:System.Printing.PrintQueue.AddJob%2A> doit s'exécuter dans un thread unique cloisonné \(STA\) toutes les fois que le paramètre <xref:System.Boolean> est `false`, ce qui doit être le cas lorsqu'une imprimante qui n'est pas une imprimante XPSDrv est utilisée.  Toutefois, l'état de cloisonnement par défaut pour [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] est plusieurs threads.  Cet état par défaut doit être inversé puisque l'exemple illustre une imprimante qui n'est pas une imprimante XPSDrv.  
  
 Il existe deux manières de modifier l'état par défaut.  L'un des moyens consiste simplement à ajouter <xref:System.STAThreadAttribute> \(autrement dit, "`[System.STAThreadAttribute()]`"\) juste au\-dessus de la première ligne de la méthode `Main` de l'application \(habituellement "`static void Main(string[] args)`"\).  Toutefois, de nombreuses applications exigent de la méthode `Main` qu'elle ait un état de cloisonnement multithread, il existe donc une deuxième méthode : placez l'appel à <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> dans un thread séparé dont l'état de cloisonnement a la valeur <xref:System.Threading.ApartmentState> avec <xref:System.Threading.Thread.SetApartmentState%2A>.  L'exemple suivant utilise cette deuxième technique.  
  
 En conséquence, l'exemple commence en instanciant un objet <xref:System.Threading.Thread> et lui passant une méthode **PrintXPS** comme paramètre <xref:System.Threading.ThreadStart>.  \(La méthode **PrintXPS** est définie ultérieurement dans l'exemple.\) Ensuite, le thread est configuré en thread unique cloisonné \(STA\).  Le seul code restant de la méthode `Main` démarre le nouveau thread.  
  
 L'essentiel de l'exemple se trouve dans la méthode `static` **BatchXPSPrinter.PrintXPS**.  Après avoir créé un serveur d'impression et une file d'attente, la méthode invite l'utilisateur à entrer un répertoire contenant des fichiers [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  Après avoir validé l'existence du répertoire et la présence de fichiers \*.xps dans celui\-ci, la méthode ajoute chacun de ces fichiers à la file d'attente à l'impression.  L'exemple supposant que l'imprimante n'est pas une imprimante XPSDrv, nous passons donc `false` au dernier paramètre de la méthode <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>.  Pour cette raison, la méthode validera le balisage [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dans le fichier avant d'essayer de le convertir en langage de description de page de l'imprimante.  Si la validation échoue, une exception est levée.  L'exemple de code interceptera l'exception, notifiera l'utilisateur à son propos, puis passera au traitement du fichier [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] suivant.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 Si vous utilisez une imprimante XPSDrv, vous pouvez alors affecter la valeur `true` au dernier paramètre.  Dans ce cas, puisque [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] est le langage de description de page de l'imprimante, la méthode enverra le fichier à l'imprimante sans le valider ou le convertir dans un autre langage.  Si vous n'êtes pas certain, au moment du design de savoir si l'application utilisera une imprimante XPSDrv ou pas, vous pouvez modifier l'application pour qu'elle lise la propriété <xref:System.Printing.PrintQueue.IsXpsDevice%2A> et crée une branche en fonction de ce qu'elle trouve.  
  
 Puisque initialement peu d'imprimantes XPSDrv seront disponibles immédiatement après la version finale de [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] et de [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], vous pouvez être amené à déguiser une imprimante qui n'est pas une imprimante XPSDrv en imprimante XPSDrv.  Pour cela, ajoutez Pipelineconfig.xml à la liste des fichiers dans la clé de Registre suivante de l'ordinateur qui exécute votre application :  
  
 HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Print\\Environments\\Windows NT x86\\Drivers\\Version\-3\\*\<PseudoXPSPrinter\>*\\DependentFiles  
  
 où *\<PseudoXPSPrinter\>* est une file d'attente à l'impression quelconque.  Puis l'ordinateur doit être redémarré.  
  
 Ce déguisement vous permettra de passer `true` comme dernier paramètre de <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> sans provoquer une exception, mais puisque *\<PseudoXPSPrinter \>* n'est pas vraiment une imprimante XPSDrv, des informations superflues seront imprimées.  
  
 **Remarque** Par simplicité, l'exemple ci\-dessus utilise la présence d'une extension \*.xps pour tester qu'un fichier est [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  Toutefois, des fichiers [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] peuvent avoir une extension différente.  L' [isXPS.exe \(isXPS Conformance Tool\)](../Topic/isXPS.exe%20\(isXPS%20Conformance%20Tool\).md) est un moyen de tester la validité [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] d'un fichier.  
  
## Voir aussi  
 <xref:System.Printing.PrintQueue>   
 <xref:System.Printing.PrintQueue.AddJob%2A>   
 <xref:System.Threading.ApartmentState>   
 <xref:System.STAThreadAttribute>   
 [XPS](http://www.microsoft.com/whdc/xps/default.mspx)   
 [Printing an XPS Document](http://msdn.microsoft.com/fr-fr/849555c8-0c4e-48c0-86bc-a5494c69b36c)   
 [Managed and Unmanaged Threading](http://msdn.microsoft.com/fr-fr/db425c20-4b2f-4433-bf96-76071c7881e5)   
 [isXPS.exe \(isXPS Conformance Tool\)](../Topic/isXPS.exe%20\(isXPS%20Conformance%20Tool\).md)   
 [Documents dans WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)   
 [Vue d'ensemble de l'impression](../../../../docs/framework/wpf/advanced/printing-overview.md)