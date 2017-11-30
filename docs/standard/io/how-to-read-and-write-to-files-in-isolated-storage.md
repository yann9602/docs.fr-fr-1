---
title: "Lecture et écriture dans des fichiers"
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
- files, isolated storage
- reading data
- storing data using isolated storage, reading and writing to files
- writing to files within store
- data storage using isolated storage, reading and writing to files
- reading files within store
- isolated storage, reading and writing to files
- data stores, reading and writing to files
- stores, reading and writing to files
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8d733efc3d70070dd12f55c651033e97d1792c38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a>Lecture et écriture dans des fichiers
Pour lire ou écrire dans un fichier dans un magasin isolé, utilisez un <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> objet avec un lecteur de flux (<xref:System.IO.StreamReader> objet) ou un writer de flux de données (<xref:System.IO.StreamWriter> objet).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant obtient un magasin isolé et vérifie l’existence d’un fichier intitulé TestStore.txt dans le magasin. S’il n’existe pas, il crée le fichier et écrit « Hello Isolated Storage » dans le fichier. Si TestStore.txt existe déjà, l’exemple de code lit à partir du fichier.  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 <xref:System.IO.FileMode?displayProperty=nameWithType>  
 <xref:System.IO.FileAccess?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader?displayProperty=nameWithType>  
 <xref:System.IO.StreamWriter?displayProperty=nameWithType>  
 [Fichier et flux de données E/S](../../../docs/standard/io/index.md)  
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)
