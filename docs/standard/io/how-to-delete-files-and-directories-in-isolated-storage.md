---
title: "Comment : supprimer des fichiers et des répertoires dans un stockage isolé"
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
- cpp
helpviewer_keywords:
- data storage using isolated storage, deleting files and directories
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, deleting files and directories
- data stores, deleting files and directories
- stores, creating files and directories
- deleting files within isolated stage file
- storing data using isolated storage, deleting files and directories
- deleting directories within isolated stage file
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 971f27cd25cbe4be3ca3fad6283ab32d4f6db0ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-delete-files-and-directories-in-isolated-storage"></a><span data-ttu-id="67380-102">Comment : supprimer des fichiers et des répertoires dans un stockage isolé</span><span class="sxs-lookup"><span data-stu-id="67380-102">How to: Delete Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="67380-103">Vous pouvez supprimer des répertoires et des fichiers dans un fichier de stockage isolé.</span><span class="sxs-lookup"><span data-stu-id="67380-103">You can delete directories and files within an isolated storage file.</span></span> <span data-ttu-id="67380-104">Dans un magasin, les noms de répertoires et de fichiers dépendent du système d’exploitation et sont spécifiées par rapport à la racine du système de fichiers virtuel.</span><span class="sxs-lookup"><span data-stu-id="67380-104">Within a store, file and directory names are operating-system dependent and are specified as relative to the root of the virtual file system.</span></span> <span data-ttu-id="67380-105">Ils ne sont pas la casse sur les systèmes d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="67380-105">They are not case-sensitive on Windows operating systems.</span></span>  
  
 <span data-ttu-id="67380-106">Le <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> classe fournit deux méthodes pour supprimer des fichiers et répertoires : <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="67380-106">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType> class supplies two methods for deleting directories and files: <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.</span></span> <span data-ttu-id="67380-107">Un <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception est levée si vous essayez de supprimer un fichier ou répertoire n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="67380-107">An <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown if you try to delete a file or directory that does not exist.</span></span> <span data-ttu-id="67380-108">Si vous incluez un caractère générique dans le nom, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> lève une <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> lève une <xref:System.ArgumentException> exception.</span><span class="sxs-lookup"><span data-stu-id="67380-108">If you include a wildcard character in the name, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> throws an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> throws an <xref:System.ArgumentException> exception.</span></span>  
  
 <span data-ttu-id="67380-109">Le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> méthode échoue si le répertoire contient des fichiers ou des sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="67380-109">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> method fails if the directory contains any files or subdirectories.</span></span> <span data-ttu-id="67380-110">Vous pouvez utiliser la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> méthodes pour extraire les fichiers existants et les répertoires.</span><span class="sxs-lookup"><span data-stu-id="67380-110">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> methods to retrieve the existing files and directories.</span></span> <span data-ttu-id="67380-111">Pour plus d’informations sur la recherche dans le système de fichiers virtuel d’un magasin, consultez [Comment : rechercher des fichiers existants et des répertoires dans un stockage isolé](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="67380-111">For more information about searching the virtual file system of a store, see [How to: Find Existing Files and Directories in Isolated Storage](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="67380-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="67380-112">Example</span></span>  
 <span data-ttu-id="67380-113">L’exemple de code suivant crée et supprime ensuite plusieurs fichiers et répertoires.</span><span class="sxs-lookup"><span data-stu-id="67380-113">The following code example creates and then deletes several directories and files.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="67380-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67380-114">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=nameWithType>  
 [<span data-ttu-id="67380-115">Stockage isolé</span><span class="sxs-lookup"><span data-stu-id="67380-115">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
