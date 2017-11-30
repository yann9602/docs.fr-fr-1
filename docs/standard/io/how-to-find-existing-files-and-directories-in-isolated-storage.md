---
title: "Comment : rechercher des fichiers et des répertoires existants dans un stockage isolé"
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
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET Framework], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET Framework], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 656c390358b6f6a671cf3ef11ea7be75f897d21c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="ab119-102">Comment : rechercher des fichiers et des répertoires existants dans un stockage isolé</span><span class="sxs-lookup"><span data-stu-id="ab119-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="ab119-103">Pour rechercher un répertoire dans un stockage isolé, utilisez le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="ab119-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ab119-104">Cette méthode prend une chaîne qui représente un modèle de recherche.</span><span class="sxs-lookup"><span data-stu-id="ab119-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="ab119-105">Vous pouvez utiliser le caractère unique ( ?) et plusieurs caractères (*) caractères génériques dans le modèle de recherche, mais les caractères génériques doivent apparaître dans la partie finale du nom.</span><span class="sxs-lookup"><span data-stu-id="ab119-105">You can use both single-character (?) and multi-character (*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="ab119-106">Par exemple, `directory1/*ect*` est une chaîne de recherche valide, mais `*ect*/directory2` n’est pas.</span><span class="sxs-lookup"><span data-stu-id="ab119-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="ab119-107">Pour rechercher un fichier, utilisez le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="ab119-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ab119-108">La restriction des caractères génériques dans des chaînes de recherche qui s’applique aux <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> s’applique également aux <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span><span class="sxs-lookup"><span data-stu-id="ab119-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="ab119-109">Aucune de ces méthodes est récursif ; la <xref:System.IO.IsolatedStorage.IsolatedStorageFile> classe ne fournit pas de méthode pour répertorier tous les répertoires ou fichiers de votre magasin.</span><span class="sxs-lookup"><span data-stu-id="ab119-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="ab119-110">Toutefois, les méthodes récursives sont affichés dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="ab119-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab119-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="ab119-111">Example</span></span>  
 <span data-ttu-id="ab119-112">L’exemple de code suivant illustre comment créer des fichiers et des répertoires dans un magasin isolé.</span><span class="sxs-lookup"><span data-stu-id="ab119-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="ab119-113">Tout d’abord, un magasin isolé par utilisateur, de domaine et d’assembly est récupéré et placé dans le `isoStore` variable.</span><span class="sxs-lookup"><span data-stu-id="ab119-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="ab119-114">Le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> méthode est utilisée pour définir quelques répertoires différents et le <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructeur crée des fichiers dans ces répertoires.</span><span class="sxs-lookup"><span data-stu-id="ab119-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="ab119-115">Le code parcourt ensuite les résultats de la `GetAllDirectories` (méthode).</span><span class="sxs-lookup"><span data-stu-id="ab119-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="ab119-116">Cette méthode utilise <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> pour rechercher tous les noms de répertoire dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="ab119-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="ab119-117">Ces noms sont stockés dans un tableau, puis `GetAllDirectories` appelle, en passant dans chaque répertoire est détecté.</span><span class="sxs-lookup"><span data-stu-id="ab119-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="ab119-118">Par conséquent, tous les noms de répertoire sont retournés dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="ab119-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="ab119-119">Ensuite, le code appelle la `GetAllFiles` (méthode).</span><span class="sxs-lookup"><span data-stu-id="ab119-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="ab119-120">Cette méthode appelle `GetAllDirectories` pour connaître les noms de tous les répertoires, puis vérifie chaque répertoire pour les fichiers à l’aide de la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="ab119-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="ab119-121">Le résultat est retourné dans un tableau pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="ab119-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="ab119-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab119-122">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="ab119-123">Stockage isolé</span><span class="sxs-lookup"><span data-stu-id="ab119-123">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
