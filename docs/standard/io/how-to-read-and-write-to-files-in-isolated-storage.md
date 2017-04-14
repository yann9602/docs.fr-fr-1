---
title: "Lecture et &#233;criture dans des fichiers | Microsoft Docs"
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
  - "stockage de données avec le stockage isolé, lire et écrire dans des fichiers"
  - "magasins de données, lire et écrire dans des fichiers"
  - "fichiers, stockage isolé"
  - "stockage isolé, lire et écrire dans des fichiers"
  - "lire des données"
  - "lire des fichiers dans un magasin"
  - "magasins, lire et écrire dans des fichiers"
  - "stocker des données à l'aide du stockage isolé, lire et écrire dans des fichiers"
  - "écrire dans les fichiers d'un magasin"
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 15
---
# Lecture et &#233;criture dans des fichiers
Pour lire, ou d'écriture, dans un fichier dans un magasin d'isolement, utilisez un objet <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> à un lecteur des entrées \(objet\)<xref:System.IO.StreamReader> \) ou en continu l'enregistreur \(objet\)<xref:System.IO.StreamWriter> \).  
  
## Exemple  
 L'exemple de code suivant obtient un magasin d'isolement et vérifie si un fichier nommé TestStore.txt existe dans le magasin.  S'il n'existe pas, il crée le fichier et écrit « hello le stockage d'isolement » dans le fichier.  Si TestStore.txt existe déjà, l'exemple de code lit à partir de le fichier.  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>   
 <xref:System.IO.FileMode?displayProperty=fullName>   
 <xref:System.IO.FileAccess?displayProperty=fullName>   
 <xref:System.IO.StreamReader?displayProperty=fullName>   
 <xref:System.IO.StreamWriter?displayProperty=fullName>   
 [Fichier et flux de données E\/S](../../../docs/standard/io/index.md)   
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)