---
title: "Obtention de magasins | Microsoft Docs"
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
  - "magasins, obtenir"
  - "stockage de données à l’aide du stockage isolé, obtenir des magasins"
  - "stockage isolé, obtenir des magasins"
  - "magasins de données, obtenir"
  - "stockage de données à l’aide du stockage isolé, obtenir des magasins"
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
caps.latest.revision: 19
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 19
---
# Obtention de magasins
Un magasin isolé expose un système de fichiers virtuel dans un compartiment de données.  La classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile> fournit plusieurs méthodes pour interagir avec un magasin d'isolement.  Pour créer et extraire des magasins, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> propose trois méthodes statiques:  
  
-   L'appel de <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> renvoie un stockage isolé par utilisateur et par assembly.  
  
-   L'appel de <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> renvoie un stockage isolé par domaine et par assembly.  
  
     Ces deux méthodes extraient un magasin qui appartient au code à partir duquel elles sont appelées.  
  
-   La méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> retourne un magasin isolé spécifié en passant une combinaison de paramètres de portée.  
  
 L'exemple de code suivant extrait un magasin qui est isolé par utilisateur, domaine et assembly.  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 Vous pouvez utiliser la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> pour spécifier qu'un magasin doit se déplacer avec un profil d'utilisateur itinérant.  Pour savoir comment mettre cela en place, consultez [Types d'isolation](../../../docs/standard/io/types-of-isolation.md).  
  
 Par défaut, des magasins isolés obtenus à partir d'assemblys distincts sont des magasins différents.  Vous pouvez accéder au magasin d'un assembly ou d'un domaine différent en passant une preuve d'assembly ou de domaine distincte comme les deux derniers paramètres de la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>.  Ceci exige une autorisation pour accéder au stockage isolé par l'identité de domaine d'application.  Pour plus d'informations, consultez la surcharge de méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>.  
  
 La méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> renvoie un nouvel objet <xref:System.IO.IsolatedStorage.IsolatedStorageFile>.  Pour déterminer le type d'isolement le mieux adapté à une situation, consultez [Types d'isolements](../../../docs/standard/io/types-of-isolation.md).  Quand vous possédez un fichier objet de stockage isolé, vous pouvez utiliser les méthodes de stockage isolé pour lire, écrire, créer et supprimer des fichiers et des répertoires de fichier.  
  
 Aucun mécanisme ne peut empêcher au code de passer un objet <xref:System.IO.IsolatedStorage.IsolatedStorageFile> au code dont l'accès est insuffisant pour obtenir lui\-même le magasin.  Les identités de domaine et d'assembly et les autorisations de stockage isolé ne sont vérifiées que lorsqu'une référence à un objet <xref:System.IO.IsolatedStorage.IsolatedStorage> est obtenue, généralement dans une méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> ou <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>.  La responsabilité de la protection de références aux objets <xref:System.IO.IsolatedStorage.IsolatedStorageFile> incombe, dès lors, au code qui utilise ces références.  
  
## Exemple  
 L'exemple de code suivant fourni un exemple très simple d'une classe obtenant un magasin qui est isolé par utilisateur et par assembly.  Le code peut être modifié afin d'extraire un magasin qui est isolé par utilisateur, par domaine et par assembly en ajoutant <xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=fullName> aux arguments passés par la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>.  
  
 Après l'exécution du code, vous pouvez confirmer qu'un magasin a été créé en tapant **StoreAdm \/LIST** à la ligne de commande.  Cela execute le [L'outil d'administration Isolated Storage \(Storeadm.exe\)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) et liste tous les magasins isolés en cours pour l'utilisateur.  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>   
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)   
 [Types d'isolation](../../../docs/standard/io/types-of-isolation.md)   
 [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)