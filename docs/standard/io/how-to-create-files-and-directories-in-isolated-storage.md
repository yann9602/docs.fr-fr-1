---
title: "Comment : créer des fichiers et des répertoires dans un stockage isolé"
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
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b8a48473bf9ac91b89657d00d27031255491353
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a><span data-ttu-id="b6422-102">Comment : créer des fichiers et des répertoires dans un stockage isolé</span><span class="sxs-lookup"><span data-stu-id="b6422-102">How to: Create Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="b6422-103">Après avoir obtenu un magasin isolé, vous pouvez créer des répertoires et fichiers pour le stockage des données.</span><span class="sxs-lookup"><span data-stu-id="b6422-103">After you have obtained an isolated store, you can create directories and files for storing data.</span></span> <span data-ttu-id="b6422-104">Dans un magasin, les noms de fichiers et de répertoires sont spécifiés par rapport à la racine du système de fichiers virtuel.</span><span class="sxs-lookup"><span data-stu-id="b6422-104">Within a store, file and directory names are specified with respect to the root of the virtual file system.</span></span>  
  
 <span data-ttu-id="b6422-105">Pour créer un répertoire, utilisez la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="b6422-105">To create a directory, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="b6422-106">Si vous spécifiez un sous-répertoire d’un répertoire qui n’existe pas, les deux répertoires sont créés.</span><span class="sxs-lookup"><span data-stu-id="b6422-106">If you specify a subdirectory of an directory that doesn't exist, both directories are created.</span></span> <span data-ttu-id="b6422-107">Si vous spécifiez un répertoire qui existe déjà, la méthode retourne sans création d’un répertoire, et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="b6422-107">If you specify a directory that already exists, the method returns without creating a directory, and no exception is thrown.</span></span> <span data-ttu-id="b6422-108">Toutefois, si vous spécifiez un nom de répertoire qui contient des caractères non valides, un <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="b6422-108">However, if you specify a directory name that contains invalid characters, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown.</span></span>  
  
 <span data-ttu-id="b6422-109">Pour créer un fichier, utilisez le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="b6422-109">To create a file, use  the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="b6422-110">Dans le système d’exploitation Windows, un fichier de stockage isolé et le répertoire respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="b6422-110">In the Windows operating system, isolated storage file and directory names are case-insensitive.</span></span> <span data-ttu-id="b6422-111">Autrement dit, si vous créez un fichier nommé `ThisFile.txt`, puis créez un autre fichier nommé `THISFILE.TXT`, qu’un seul fichier est créé.</span><span class="sxs-lookup"><span data-stu-id="b6422-111">That is, if you create a file named `ThisFile.txt`, and then create another file named `THISFILE.TXT`, only one file is created.</span></span> <span data-ttu-id="b6422-112">Le nom de fichier conserve sa casse d’origine pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="b6422-112">The file name keeps its original casing for display purposes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6422-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6422-113">Example</span></span>  
 <span data-ttu-id="b6422-114">L’exemple de code suivant illustre comment créer des fichiers et des répertoires dans un magasin isolé.</span><span class="sxs-lookup"><span data-stu-id="b6422-114">The following code example illustrates how to create files and directories in an isolated store.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b6422-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6422-115">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [<span data-ttu-id="b6422-116">Stockage isolé</span><span class="sxs-lookup"><span data-stu-id="b6422-116">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
