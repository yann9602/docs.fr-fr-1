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
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="7292b-102">Comment : énumérer des répertoires et des fichiers</span><span class="sxs-lookup"><span data-stu-id="7292b-102">How to: Enumerate Directories and Files</span></span>
<span data-ttu-id="7292b-103">Vous pouvez énumérer des répertoires et des fichiers à l’aide des méthodes qui retournent une collection énumérable de chaînes de leurs noms.</span><span class="sxs-lookup"><span data-stu-id="7292b-103">You can enumerate directories and files by using methods that return an enumerable collection of strings of their names.</span></span> <span data-ttu-id="7292b-104">Vous pouvez également utiliser des méthodes qui retournent une collection énumérable de <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, ou <xref:System.IO.FileSystemInfo> objets.</span><span class="sxs-lookup"><span data-stu-id="7292b-104">You can also use methods that return an enumerable collection of <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span> <span data-ttu-id="7292b-105">Les collections énumérables offrent de meilleures performances que les tableaux lorsque vous travaillez avec grandes collections de fichiers et répertoires.</span><span class="sxs-lookup"><span data-stu-id="7292b-105">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span>  
  
 <span data-ttu-id="7292b-106">Vous pouvez également utiliser les collections énumérables obtenues à partir de ces méthodes pour fournir le <xref:System.Collections.Generic.IEnumerable%601> paramètre pour les constructeurs de collection de classes telles que la <xref:System.Collections.Generic.List%601> classe.</span><span class="sxs-lookup"><span data-stu-id="7292b-106">You can also use enumerable collections obtained from these methods to supply the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes such as the <xref:System.Collections.Generic.List%601> class.</span></span>  
  
 <span data-ttu-id="7292b-107">Si vous souhaitez obtenir uniquement les noms de répertoires ou fichiers, utilisez les méthodes d’énumération de la <xref:System.IO.Directory> classe.</span><span class="sxs-lookup"><span data-stu-id="7292b-107">If you want to obtain only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="7292b-108">Si vous souhaitez obtenir d’autres propriétés des répertoires ou fichiers, utilisez le <xref:System.IO.DirectoryInfo> et <xref:System.IO.FileSystemInfo> classes.</span><span class="sxs-lookup"><span data-stu-id="7292b-108">If you want to obtain other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
 <span data-ttu-id="7292b-109">Le tableau suivant fournit un guide sur les méthodes qui retournent des collections énumérables.</span><span class="sxs-lookup"><span data-stu-id="7292b-109">The following table provides a guide to the methods that return enumerable collections.</span></span>  
  
|<span data-ttu-id="7292b-110">Pour énumérer</span><span class="sxs-lookup"><span data-stu-id="7292b-110">To enumerate</span></span>|<span data-ttu-id="7292b-111">Collection énumérable à retourner</span><span class="sxs-lookup"><span data-stu-id="7292b-111">Enumerable collection to return</span></span>|<span data-ttu-id="7292b-112">Méthode à utiliser</span><span class="sxs-lookup"><span data-stu-id="7292b-112">Method to use</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="7292b-113">Répertoires</span><span class="sxs-lookup"><span data-stu-id="7292b-113">Directories</span></span>|<span data-ttu-id="7292b-114">Noms de répertoires</span><span class="sxs-lookup"><span data-stu-id="7292b-114">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="7292b-115">Informations d’annuaire (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="7292b-115">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7292b-116">Fichiers</span><span class="sxs-lookup"><span data-stu-id="7292b-116">Files</span></span>|<span data-ttu-id="7292b-117">Noms de fichiers</span><span class="sxs-lookup"><span data-stu-id="7292b-117">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="7292b-118">Informations sur les fichiers (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="7292b-118">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7292b-119">Informations de système de fichiers</span><span class="sxs-lookup"><span data-stu-id="7292b-119">File system information</span></span>|<span data-ttu-id="7292b-120">Entrées de système de fichiers</span><span class="sxs-lookup"><span data-stu-id="7292b-120">File system entries</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="7292b-121">Informations de système de fichiers (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="7292b-121">File system information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="7292b-122">Bien que vous puissiez énumérer immédiatement tous les fichiers dans les sous-répertoires d’un répertoire parent à l’aide de la <xref:System.IO.SearchOption.AllDirectories> recherche option fournie par le <xref:System.IO.SearchOption> énumération, les exceptions d’accès non autorisé (<xref:System.UnauthorizedAccessException>) peut entraîner une énumération ne pas être complets.</span><span class="sxs-lookup"><span data-stu-id="7292b-122">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> search option provided by the <xref:System.IO.SearchOption> enumeration, unauthorized access exceptions (<xref:System.UnauthorizedAccessException>) may cause the enumeration to be incomplete.</span></span> <span data-ttu-id="7292b-123">Si ces exceptions sont possibles, vous pouvez les intercepter et continuer en commençant par énumérer les répertoires, puis les fichiers.</span><span class="sxs-lookup"><span data-stu-id="7292b-123">If these exceptions are possible, you can catch them and continue by first enumerating directories and then enumerating files.</span></span>  
  
### <a name="to-enumerate-directory-names"></a><span data-ttu-id="7292b-124">Pour énumérer les noms de répertoires</span><span class="sxs-lookup"><span data-stu-id="7292b-124">To enumerate directory names</span></span>  
  
-   <span data-ttu-id="7292b-125">Utilisez la <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> méthode pour obtenir une liste des noms de répertoire de niveau supérieur dans un chemin d’accès spécifié.</span><span class="sxs-lookup"><span data-stu-id="7292b-125">Use the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to obtain a list of the top-level directory names in a specified path.</span></span>  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a><span data-ttu-id="7292b-126">Pour énumérer les noms de fichiers dans un répertoire et les sous-répertoires</span><span class="sxs-lookup"><span data-stu-id="7292b-126">To enumerate file names in a directory and subdirectories</span></span>  
  
-   <span data-ttu-id="7292b-127">Utilisez la <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> méthode pour rechercher un répertoire et (éventuellement) de ses sous-répertoires et pour obtenir une liste de noms de fichiers qui correspondent à un modèle de recherche spécifié.</span><span class="sxs-lookup"><span data-stu-id="7292b-127">Use the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to search a directory and (optionally) its subdirectories, and to obtain a list of file names that match a specified search pattern.</span></span>  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a><span data-ttu-id="7292b-128">Pour énumérer une collection d’objets DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="7292b-128">To enumerate a collection of DirectoryInfo objects</span></span>  
  
-   <span data-ttu-id="7292b-129">Utilisez la <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> méthode pour obtenir une collection de répertoires de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="7292b-129">Use the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to obtain a collection of top-level directories.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a><span data-ttu-id="7292b-130">Pour énumérer une collection d’objets FileInfo dans tous les répertoires</span><span class="sxs-lookup"><span data-stu-id="7292b-130">To enumerate a collection of FileInfo objects in all directories</span></span>  
  
-   <span data-ttu-id="7292b-131">Utilisez la <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> méthode pour obtenir une collection de fichiers qui correspondent à un modèle de recherche spécifié dans tous les répertoires.</span><span class="sxs-lookup"><span data-stu-id="7292b-131">Use the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to obtain a collection of files that match a specified search pattern in all directories.</span></span> <span data-ttu-id="7292b-132">Cet exemple énumère d’abord les répertoires de niveau supérieur pour intercepter les exceptions de tout accès non autorisé, puis énumère les fichiers.</span><span class="sxs-lookup"><span data-stu-id="7292b-132">This example first enumerates the top-level directories to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7292b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7292b-133">See Also</span></span>  
 [<span data-ttu-id="7292b-134">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="7292b-134">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
