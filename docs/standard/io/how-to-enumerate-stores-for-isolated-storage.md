---
title: "Énumération de magasins"
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
- enumerating stores
- data storage using isolated storage, enumerating stores
- storing data using isolated storage, enumerating stores
- stores, enumerating
- isolated storage, enumerating stores
- data stores, enumerating
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8f8863f1d8b3c7f4ed8f65f8f8eb3e8af51b0405
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-stores-for-isolated-storage"></a>Énumération de magasins
Vous pouvez énumérer tous les magasins isolés pour l’utilisateur actuel à l’aide de la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=nameWithType> méthode statique. Cette méthode prend un <xref:System.IO.IsolatedStorage.IsolatedStorageScope> valeur et retourne un <xref:System.IO.IsolatedStorage.IsolatedStorageFile> énumérateur. Pour énumérer des magasins, vous devez avoir le <xref:System.Security.Permissions.IsolatedStorageFilePermission> autorisation qui spécifie la <xref:System.Security.Permissions.IsolatedStorageContainment.AdministerIsolatedStorageByUser> valeur. Si vous appelez le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> méthode avec la <xref:System.IO.IsolatedStorage.IsolatedStorageScope.User> valeur, elle retourne un tableau de <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objets qui sont définis pour l’utilisateur actuel.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant obtient un magasin qui est isolé par utilisateur et par assembly et crée des fichiers récupère ces fichiers à l’aide de la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> (méthode).  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)
