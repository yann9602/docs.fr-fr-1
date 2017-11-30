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
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a>Comment : rechercher des fichiers et des répertoires existants dans un stockage isolé
Pour rechercher un répertoire dans un stockage isolé, utilisez le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> (méthode). Cette méthode prend une chaîne qui représente un modèle de recherche. Vous pouvez utiliser le caractère unique ( ?) et plusieurs caractères (*) caractères génériques dans le modèle de recherche, mais les caractères génériques doivent apparaître dans la partie finale du nom. Par exemple, `directory1/*ect*` est une chaîne de recherche valide, mais `*ect*/directory2` n’est pas.  
  
 Pour rechercher un fichier, utilisez le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> (méthode). La restriction des caractères génériques dans des chaînes de recherche qui s’applique aux <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> s’applique également aux <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.  
  
 Aucune de ces méthodes est récursif ; la <xref:System.IO.IsolatedStorage.IsolatedStorageFile> classe ne fournit pas de méthode pour répertorier tous les répertoires ou fichiers de votre magasin. Toutefois, les méthodes récursives sont affichés dans l’exemple de code suivant.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre comment créer des fichiers et des répertoires dans un magasin isolé. Tout d’abord, un magasin isolé par utilisateur, de domaine et d’assembly est récupéré et placé dans le `isoStore` variable. Le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> méthode est utilisée pour définir quelques répertoires différents et le <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructeur crée des fichiers dans ces répertoires. Le code parcourt ensuite les résultats de la `GetAllDirectories` (méthode). Cette méthode utilise <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> pour rechercher tous les noms de répertoire dans le répertoire actif. Ces noms sont stockés dans un tableau, puis `GetAllDirectories` appelle, en passant dans chaque répertoire est détecté. Par conséquent, tous les noms de répertoire sont retournés dans un tableau. Ensuite, le code appelle la `GetAllFiles` (méthode). Cette méthode appelle `GetAllDirectories` pour connaître les noms de tous les répertoires, puis vérifie chaque répertoire pour les fichiers à l’aide de la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> (méthode). Le résultat est retourné dans un tableau pour l’affichage.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)
