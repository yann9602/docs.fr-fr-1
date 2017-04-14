---
title: "Comment&#160;: anticiper des conditions d&#39;espace insuffisant avec le stockage isol&#233; | Microsoft Docs"
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
  - "magasins de données, quotas"
  - "stockage isolé, quotas"
  - "quantité de stockage isolé utilisé"
  - "limite sur le stockage isolé utilisé"
  - "magasins, quotas"
  - "magasins, conditions d’espace insuffisant"
  - "stockage de données avec le stockage isolé, quotas"
  - "stocker des données avec le stockage isolé, quotas"
  - "espace restant dans un stockage isolé"
  - "magasins de données, conditions d’espace insuffisant"
  - "stocker des données avec le stockage isolé, conditions d’espace insuffisant"
  - "quotas pour le stockage isolé"
  - "stockage isolé, conditions d’espace insuffisant"
  - "stockage de données avec le stockage isolé, conditions d’espace insuffisant"
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: anticiper des conditions d&#39;espace insuffisant avec le stockage isol&#233;
Le code qui utilise le stockage isolé est limité par un [quota](../../../docs/standard/io/isolated-storage.md#quotas) qui spécifie la taille maximale du compartiment de données qui comprend les fichiers et les répertoires de stockage isolé.  Ce quota est définie par la stratégie de sécurité et peut être configurée par les administrateurs.  Si la taille maximale autorisée est dépassée lors d'une tentative d'écriture de données, une exception <xref:System.IO.IsolatedStorage.IsolatedStorageException> est levée et l'opération échoue.  Ceci vous aide à éviter des attaques par déni de service malveillantes qui pourraient entraîner l'application à refuser des demandes, car le stockage des données est rempli.  
  
 Pour vous aider à déterminer si une tentative d'écriture donnée peut échouer pour cette raison, la classe <xref:System.IO.IsolatedStorage.IsolatedStorage> propose trois propriétés en lecture seule : <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.  Vous pouvez utiliser ces propriétés pour déterminer si l'écriture dans le magasin peut entraîner le dépassement de la taille maximale autorisée du magasin.  Souvenez\-vous ,lorsque vous utilisez ces propriétés, que le stockage isolé est accessible simultanément ; ainsi, si vous calculez l'espace de stockage restant, il se peut que l'espace de stockage soit consommé lorsque vous tentez d'écrire dans le magasin.  Toutefois, vous pouvez utiliser la taille maximale du magasin pour vous aider à déterminer si la limite supérieure du stockage disponible va être atteinte.  
  
 La propriété <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> dépend de la preuve de l'assembly de fonctionner correctement.  Par conséquent, cette propriété doit uniquement être récupérée sur des objets <xref:System.IO.IsolatedStorage.IsolatedStorageFile> ayant été créés à l'aide de la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, ou <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>.  Les objets <xref:System.IO.IsolatedStorage.IsolatedStorageFile> ayant été créés d'une autre façon \(par exemple, les objets ayant été retournés par la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> \) retourneront une taille maximale incorrecte.  
  
## Exemple  
 L'exemple de code suivant obtient un magasin isolé, crée des fichiers et récupère la propriété <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>.  L'espace restant est calculé en octets.  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)   
 [Obtention de magasins](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)