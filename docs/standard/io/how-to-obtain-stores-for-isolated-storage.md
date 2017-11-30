---
title: Obtention de magasins
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
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb0b877aa0f4cee36bd1f8c1cea624cf9368fbaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a>Obtention de magasins
Un magasin isolé expose un système de fichiers virtuel dans un compartiment de données. La <xref:System.IO.IsolatedStorage.IsolatedStorageFile> classe fournit plusieurs méthodes pour interagir avec un magasin isolé. Pour créer et extraire des magasins, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> propose trois méthodes statiques :  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>Retourne un stockage isolé par utilisateur et par assembly.  
  
-   <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>Retourne un stockage isolé par domaine et par assembly.  
  
     Les deux méthodes récupèrent un magasin qui appartient au code à partir de laquelle elles sont appelées.  
  
-   La méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> retourne un magasin isolé spécifié en passant une combinaison de paramètres de portée.  
  
 Le code suivant retourne un magasin isolé par utilisateur, assembly et le domaine.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Vous pouvez utiliser la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> méthode pour spécifier qu’un magasin doit se déplacer avec un profil utilisateur itinérant. Pour plus d’informations sur la façon de configurer ce paramètre, consultez [Types d’Isolation](../../../docs/standard/io/types-of-isolation.md).  
  
 Les magasins isolés obtenues dans des assemblys différents sont, par défaut, des magasins différents. Vous pouvez accéder au magasin d’un domaine ou un autre assembly en passant la preuve d’assembly ou de domaine dans les paramètres de la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> (méthode). Requiert l’autorisation pour accéder au stockage isolé par l’identité de domaine d’application. Pour plus d’informations, consultez le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> surcharges de méthode.  
  
 Le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> méthodes retournent un <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objet. Pour vous aider à déterminer le type d’isolation le plus approprié à votre situation, consultez [Types d’Isolation](../../../docs/standard/io/types-of-isolation.md). Lorsque vous disposez d’un objet de fichier de stockage isolé, vous pouvez utiliser les méthodes de stockage isolé pour lire, écrire, créer et supprimer des fichiers et répertoires.  
  
 Il n’existe aucun mécanisme qui empêche le code de passage une <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objet vers du code qui n’a pas de droits d’accès nécessaires pour obtenir le magasin lui-même. Les identités de domaine et d’assembly et les autorisations de stockage isolé sont vérifiées uniquement lorsqu’une référence à un <xref:System.IO.IsolatedStorage.IsolatedStorage> objet est obtenu en général, dans le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, ou <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> (méthode). Protection de références aux <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objets est, par conséquent, la responsabilité du code qui utilise ces références.  
  
## <a name="example"></a>Exemple  
 Le code suivant fournit un exemple simple d’une classe obtenant un magasin isolé par utilisateur et par assembly. Le code peut être modifié afin d’extraire un magasin isolé par utilisateur, domaine et par assembly en ajoutant <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> aux arguments qui la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> passe de la méthode.  
  
 Une fois que vous exécutez le code, vous pouvez confirmer qu’un magasin a été créé en tapant **StoreAdm /LIST** à la ligne de commande. Cette commande exécute le [outil Isolated Storage (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) et répertorie tous les stocke les actuel isolé pour l’utilisateur.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)  
 [Types d’isolation](../../../docs/standard/io/types-of-isolation.md)  
 [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
