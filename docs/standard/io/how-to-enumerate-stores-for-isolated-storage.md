---
title: "&#201;num&#233;ration de magasins | Microsoft Docs"
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
  - "énumérer des magasins"
  - "stockage de données à l’aide du stockage isolé, énumérer des magasins"
  - "stocker des données à l’aide du stockage isolé, énumérer des magasins"
  - "magasins, énumérer"
  - "stockage isolé, énumérer des magasins"
  - "magasins de données, énumérer"
ms.assetid: 0fcf279a-f241-48f0-8034-2e3d331f1fcb
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# &#201;num&#233;ration de magasins
Vous pouvez énumérer tous les magasins isolés pour l'utilisateur actuel à l'aide de la méthode statique  <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A?displayProperty=fullName>.  Cette méthode accepte une valeur <xref:System.IO.IsolatedStorage.IsolatedStorageScope> et renvoie un énumérateur <xref:System.IO.IsolatedStorage.IsolatedStorageFile>.  Pour énumérer des magasins, vous devez avoir l'autorisation <xref:System.Security.Permissions.IsolatedStorageFilePermission> dont la valeur est <xref:System.Security.Permissions.IsolatedStorageContainment>.  Si vous appelez la méthode de <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> avec la valeur <xref:System.IO.IsolatedStorage.IsolatedStorageScope>, elle renvoie un tableau d'objets <xref:System.IO.IsolatedStorage.IsolatedStorageFile> définis pour l'utilisateur actuel.  
  
## Exemple  
 L'exemple de code suivant obtient un magasin qui est détachée par l'utilisateur et l'assembly, crée des fichiers, et récupère ces fichiers à l'aide de la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A>.  
  
 [!code-csharp[Conceptual.IsolatedStorage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source2.cs#2)]
 [!code-vb[Conceptual.IsolatedStorage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source2.vb#2)]  
  
## Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)