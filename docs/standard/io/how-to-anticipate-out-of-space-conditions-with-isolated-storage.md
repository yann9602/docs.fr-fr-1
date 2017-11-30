---
title: "Comment : anticiper des conditions d'espace insuffisant avec le stockage isolé"
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
- data stores, quotas
- isolated storage, quotas
- quanitity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d813522d0aeb9bf37582c167760d44268df27039
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a>Comment : anticiper des conditions d'espace insuffisant avec le stockage isolé
Le code qui utilise le stockage isolé est limité par un [quota](../../../docs/standard/io/isolated-storage.md#quotas) qui spécifie la taille maximale du compartiment de données dans laquelle isolé des fichiers de stockage et de répertoires existent. Le quota est défini par la stratégie de sécurité et peut être configuré par les administrateurs. Si la valeur maximale autorisée de taille est dépassée lors de la tentative d’écriture de données, un <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception est levée et l’opération échoue. Cela permet d’éviter les attaques par déni de service qui peut entraîner l’application à refuser des demandes, car le stockage des données est rempli.  
  
 Pour vous aider à déterminer si une tentative d’écriture donnée peut échouer pour cette raison, le <xref:System.IO.IsolatedStorage.IsolatedStorage> classe fournit les trois propriétés en lecture seule : <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, et <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>. Vous pouvez utiliser ces propriétés pour déterminer si l’écriture dans le magasin peut entraîner la taille maximale autorisée de la banque de dépassement. N’oubliez pas que le stockage isolé est accessible simultanément ; Par conséquent, lorsque vous calculez la quantité de stockage restant, l’espace de stockage pouvant être consommé par le temps que vous tentez d’écrire dans le magasin. Toutefois, vous pouvez utiliser la taille maximale de la banque pour aider à déterminer si la limite maximale de stockage disponible est sur le point d’être atteint.  
  
 Le <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> propriété dépend de la preuve de l’assembly fonctionne correctement. Pour cette raison, vous devez récupérer cette propriété uniquement sur <xref:System.IO.IsolatedStorage.IsolatedStorageFile> les objets qui ont été créés à l’aide de la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, ou <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> (méthode). <xref:System.IO.IsolatedStorage.IsolatedStorageFile>les objets qui ont été créés dans une autre façon (par exemple, les objets retournés à partir de la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> (méthode)) ne retourne pas une taille maximale.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant obtient un magasin isolé, crée des fichiers et récupère la <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> propriété. L’espace restant est indiqué en octets.  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)  
 [Obtention de magasins](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
