---
title: "Comment : énumérer des répertoires et des fichiers"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: caf9bdec017a5466269ff7fe97be4d0243035b4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enumerate-directories-and-files"></a>Comment : énumérer des répertoires et des fichiers
Vous pouvez énumérer des répertoires et des fichiers à l’aide des méthodes qui retournent une collection énumérable de chaînes de leurs noms. Vous pouvez également utiliser des méthodes qui retournent une collection énumérable de <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, ou <xref:System.IO.FileSystemInfo> objets. Les collections énumérables offrent de meilleures performances que les tableaux lorsque vous travaillez avec grandes collections de fichiers et répertoires.  
  
 Vous pouvez également utiliser les collections énumérables obtenues à partir de ces méthodes pour fournir le <xref:System.Collections.Generic.IEnumerable%601> paramètre pour les constructeurs de collection de classes telles que la <xref:System.Collections.Generic.List%601> classe.  
  
 Si vous souhaitez obtenir uniquement les noms de répertoires ou fichiers, utilisez les méthodes d’énumération de la <xref:System.IO.Directory> classe. Si vous souhaitez obtenir d’autres propriétés des répertoires ou fichiers, utilisez le <xref:System.IO.DirectoryInfo> et <xref:System.IO.FileSystemInfo> classes.  
  
 Le tableau suivant fournit un guide sur les méthodes qui retournent des collections énumérables.  
  
|Pour énumérer|Collection énumérable à retourner|Méthode à utiliser|  
|------------------|-------------------------------------|-------------------|  
|Répertoires|Noms de répertoires|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||Informations d’annuaire (<xref:System.IO.DirectoryInfo>)|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|Fichiers|Noms de fichiers|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||Informations sur les fichiers (<xref:System.IO.FileInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|Informations de système de fichiers|Entrées de système de fichiers|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||Informations de système de fichiers (<xref:System.IO.FileSystemInfo>)|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 Bien que vous puissiez énumérer immédiatement tous les fichiers dans les sous-répertoires d’un répertoire parent à l’aide de la <xref:System.IO.SearchOption.AllDirectories> recherche option fournie par le <xref:System.IO.SearchOption> énumération, les exceptions d’accès non autorisé (<xref:System.UnauthorizedAccessException>) peut entraîner une énumération ne pas être complets. Si ces exceptions sont possibles, vous pouvez les intercepter et continuer en commençant par énumérer les répertoires, puis les fichiers.  
  
### <a name="to-enumerate-directory-names"></a>Pour énumérer les noms de répertoires  
  
-   Utilisez la <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> méthode pour obtenir une liste des noms de répertoire de niveau supérieur dans un chemin d’accès spécifié.  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a>Pour énumérer les noms de fichiers dans un répertoire et les sous-répertoires  
  
-   Utilisez la <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> méthode pour rechercher un répertoire et (éventuellement) de ses sous-répertoires et pour obtenir une liste de noms de fichiers qui correspondent à un modèle de recherche spécifié.  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a>Pour énumérer une collection d’objets DirectoryInfo  
  
-   Utilisez la <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> méthode pour obtenir une collection de répertoires de niveau supérieur.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a>Pour énumérer une collection d’objets FileInfo dans tous les répertoires  
  
-   Utilisez la <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> méthode pour obtenir une collection de fichiers qui correspondent à un modèle de recherche spécifié dans tous les répertoires. Cet exemple énumère d’abord les répertoires de niveau supérieur pour intercepter les exceptions de tout accès non autorisé, puis énumère les fichiers.  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier et flux de données E/S](../../../docs/standard/io/index.md)
