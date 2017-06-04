---
title: "E/S sur fichier asynchrones | Microsoft Docs"
ms.custom: ""
ms.date: "03/03/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "flux synchrones"
  - "E/S asynchrones"
  - "E/S synchrones"
  - "flux asynchrones"
  - "E/S (.NET Framework), E/S asynchrones"
  - "classe Stream, E/S synchrones"
  - "flux de données, flux asynchrones"
  - "classe Stream, E/S asynchrones"
  - "demandes d'E/S multiples"
  - "flux de données, flux synchrones"
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
caps.latest.revision: 23
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
---
# E/S sur fichier asynchrones
Les opérations asynchrones vous permettent d'exécuter des opérations d'E\/S consommant beaucoup de ressources sans bloquer le thread principal. Cette considération de performance est particulièrement importante dans une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ou une application [!INCLUDE[desktop_appname](../../../includes/desktop-appname-md.md)] où une longue opération de flux peut bloquer le thread d'interface utilisateur et faire que l'application s'affiche comme si elle ne fonctionnait pas.  
  
 Depuis le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les types d'E\/S incluent des méthodes async pour simplifier les opérations asynchrones. Une méthode asynchrone contient `Async` dans son nom, comme <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, et <xref:System.IO.TextReader.ReadToEndAsync%2A>. Ces méthodes asynchrones sont implémentées sur les classes de flux, telles que <xref:System.IO.Stream>, <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, et les classes qui sont utilisées pour lire ou écrire dans des flux, comme <xref:System.IO.TextReader> et l'<xref:System.IO.TextWriter>.  
  
 Dans .NET Framework 4 et les versions antérieures, on doit utiliser des méthodes telles que <xref:System.IO.Stream.BeginRead%2A> et <xref:System.IO.Stream.EndRead%2A> pour implémenter les opérations d'E\/S asynchrones. Ces méthodes sont toujours disponibles dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] pour prendre en charge le code hérité. Toutefois, les méthodes asynchrones vous aident à implémenter les opérations d'E\/S asynchrones plus facilement.  
  
 Depuis le [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], Visual Studio fournit deux mots clés pour la programmation asynchrone :  
  
-   `Async` \(Visual Basic\) ou `async` modificateur \(C\#\), qui est utilisé pour marquer une méthode contenant une opération asynchrone.  
  
-   `Await` \(Visual Basic\) ou `await` opérateur \(C\#\), qui est appliqué au résultat d'une méthode asynchrone.  
  
 Pour implémenter des opérations d'E\/S asynchrones, utilisez ces mots clés conjointement aux méthodes async, comme indiqué dans les exemples suivants. Pour plus d'informations, consultez [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
 L'exemple suivant montre comment utiliser deux objets <xref:System.IO.FileStream> pour copier des fichiers de façon asynchrone d'un répertoire à un autre. Notez que le gestionnaire d'événements <xref:System.Web.UI.WebControls.Button.Click> pour le contrôle <xref:System.Windows.Controls.Button> est marqué avec le modificateur `async` car il appelle une méthode asynchrone.  
  
 [!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
 [!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]  
  
 L'exemple suivant est semblable au précédent, mais utilise des objets <xref:System.IO.StreamReader> et <xref:System.IO.StreamWriter> pour lire et écrire le contenu d'un fichier texte de façon asynchrone.  
  
 [!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
 [!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]  
  
 L'exemple suivant montre le fichier code\-behind et le fichier XAML utilisés pour ouvrir un fichier comme <xref:System.IO.Stream> dans une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], et lire son contenu en utilisant une instance de la classe <xref:System.IO.StreamReader>. Il utilise des méthodes asynchrones pour ouvrir le fichier en tant que flux et lire son contenu.  
  
 [!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
 [!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]  
  
 [!code-xml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]  
  
## Voir aussi  
 <xref:System.IO.Stream>   
 [Fichier et flux de données E\/S](../../../docs/standard/io/index.md)   
 [Programmation asynchrone avec Async et Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)