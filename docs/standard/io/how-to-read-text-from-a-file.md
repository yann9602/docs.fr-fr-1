---
title: "Comment&#160;: lire du texte dans un fichier | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "flux de données, lire du texte à partir de fichiers"
  - "E/S (.NET Framework), lire du texte à partir de fichiers"
  - "lire des données, fichiers texte"
  - "lire des fichiers texte"
  - "flux, lire du texte à partir de fichiers"
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
caps.latest.revision: 23
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 23
---
# Comment&#160;: lire du texte dans un fichier
Les exemples suivants montrent comment lire le texte de façon synchrone et asynchrone à partir d'un fichier texte à l'aide du .NET pour les applications de bureau.  Dans les deux exemples, lorsque vous créez l'instance de la classe <xref:System.IO.StreamReader>, vous fournissez le chemin d'accès relatif ou absolu au fichier.  Les exemples suivants supposent que le fichier nommé TestFile.txt se trouve dans le même dossier que l'application.  
  
 Ces exemples de code ne s'appliquent pas à développer des applications Windows Store car le Windows Runtime fournit différents types de flux de lecture et d'écriture aux fichiers.  Pour un exemple qui montre comment lire le texte d'un fichier dans le contexte d'une application du Windows Store, consultez [Démarrage rapide : lecture et écriture de fichiers](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx).  Pour des exemples qui montrent comment effectuer une conversion entre des flux .NET Framework et des flux Windows Runtime, consultez [Comment : effectuer une conversion entre les flux .NET Framework et les flux Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).  
  
## Exemple  
 Le premier exemple montre une opération synchrone de lecture dans une application console.  Dans cet exemple, le fichier texte est ouvert à l'aide d'un lecteur de flux, le contenu est copié dans une chaîne et la chaîne est affichée dans la console.  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## Exemple  
 Le deuxième exemple présente une opération asynchrone de lecture dans une application Windows Presentation Foundation \(WPF\).  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## Voir aussi  
 <xref:System.IO.StreamReader>   
 <xref:System.IO.File.OpenText%2A?displayProperty=fullName>   
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName>   
 [E\/S sur fichier asynchrones](../../../docs/standard/io/e-s-sur-fichier-asynchrones.md)   
 [NIB: How to: Create a Directory Listing](http://msdn.microsoft.com/fr-fr/4d2772b1-b991-4532-a8a6-6ef733277e69)   
 [Démarrage rapide : lecture et écriture de fichiers](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx)   
 [Comment : effectuer une conversion entre les flux .NET Framework et les flux Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)   
 [Comment : lire et écrire dans un fichier de données créé récemment](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)   
 [Comment : ouvrir un fichier journal et y ajouter des éléments](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)   
 [Comment : écrire du texte dans un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)   
 [Comment : lire les caractères d'une chaîne](../../../docs/standard/io/how-to-read-characters-from-a-string.md)   
 [Comment : écrire des caractères dans une chaîne](../../../docs/standard/io/how-to-write-characters-to-a-string.md)   
 [Fichier et flux de données E\/S](../../../docs/standard/io/index.md)