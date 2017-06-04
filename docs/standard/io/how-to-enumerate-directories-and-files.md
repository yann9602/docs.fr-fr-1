---
title: "Comment&#160;: &#233;num&#233;rer des r&#233;pertoires et des fichiers | Microsoft Docs"
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
  - "E/S (.NET Framework), énumération des répertoires et des fichiers"
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: 18
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: &#233;num&#233;rer des r&#233;pertoires et des fichiers
Vous pouvez énumérer des répertoires et des fichiers à l'aide de méthodes qui retournent une collection énumérable de chaînes de leurs noms.  Vous pouvez également utiliser des méthodes qui retournent une collection énumérable d'objets <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo> ou <xref:System.IO.FileSystemInfo>.  Les collections énumérables offrent de meilleures performances que les tables lorsque vous travaillez avec des collections de répertoires et de fichiers.  
  
 Vous pouvez également utiliser les collections énumérables obtenues à partir de ces méthodes pour fournir le paramètre <xref:System.Collections.Generic.IEnumerable%601> pour les constructeurs de classes de collection telles que la classe <xref:System.Collections.Generic.List%601>.  
  
 Si vous voulez obtenir uniquement les noms de répertoires ou fichiers, utilisez les méthodes d'énumération de la classe <xref:System.IO.Directory>.  Si vous voulez obtenir d'autres propriétés des répertoires ou fichiers, utilisez les classes <xref:System.IO.FileSystemInfo> et <xref:System.IO.DirectoryInfo>.  
  
 Le tableau suivant fournit un guide pour les méthodes qui retournent des collections énumérables.  
  
|Pour énumérer|Collection énumérable à retourner|Méthode à utiliser|  
|-------------------|---------------------------------------|------------------------|  
|Répertoires|Noms de répertoires|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=fullName>|  
||Informations sur le répertoire \(<xref:System.IO.DirectoryInfo>\)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=fullName>|  
|Fichiers|Noms de fichiers|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=fullName>|  
||Informations sur le fichier \(<xref:System.IO.FileInfo>\)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=fullName>|  
|Informations sur le système de fichiers|Entrées du système de fichiers|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=fullName>|  
||Informations sur le système de fichiers \(<xref:System.IO.FileSystemInfo>\)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=fullName>|  
  
 Bien que vous puissiez énumérer immédiatement tous les fichiers des sous\-répertoires d'un répertoire parent à l'aide de l'option de recherche <xref:System.IO.SearchOption> fournit par l'énumération <xref:System.IO.SearchOption>, les exceptions d'accès non autorisé \(<xref:System.UnauthorizedAccessException>\) peuvent entraîner une énumération incomplète.  Si ces exceptions sont possibles, vous pouvez les intercepter et continuer en commençant par énumérer les répertoires, puis les fichiers.  
  
### Pour énumérer des noms de répertoires  
  
-   Utilisez la méthode <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=fullName> pour obtenir la liste des noms de répertoires de niveau supérieur dans un chemin d'accès spécifié.  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### Pour énumérer les noms de fichier dans un répertoire et les sous\-répertoires  
  
-   Utilisez la méthode <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=fullName> pour rechercher dans un répertoire et ses répertoires enfants et obtenir la liste des noms de fichiers figurant dans un chemin d'accès spécifié qui correspondent à un modèle de recherche spécifié.  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### Pour énumérer une collection d'objets DirectoryInfo  
  
-   Utilisez la méthode <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=fullName> pour obtenir une collection de répertoires de niveau supérieur.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### Pour énumérer une collection d'objets FileInfo dans tous les répertoires  
  
-   Utilisez la méthode <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=fullName> pour obtenir une collection des fichiers qui correspondent à un modèle de recherche spécifié dans tous les répertoires.  Cet exemple énumère d'abord les répertoires de niveau supérieur pour intercepter les exceptions d'accès non autorisé possibles, puis énumère les fichiers.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## Voir aussi  
 [Fichier et flux de données E\/S](../../../docs/standard/io/index.md)