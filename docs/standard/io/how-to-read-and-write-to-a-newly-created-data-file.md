---
title: "Comment&#160;: lire et &#233;crire dans un fichier de donn&#233;es cr&#233;&#233; r&#233;cemment | Microsoft Docs"
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
  - "BinaryReader (classe), exemples"
  - "BinaryWriter (classe), exemples"
  - "E/S (.NET Framework), lire des données"
  - "E/S (.NET Framework), écrire des données"
  - "flux, lire et écrire des données"
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: lire et &#233;crire dans un fichier de donn&#233;es cr&#233;&#233; r&#233;cemment
Les classes <xref:System.IO.BinaryWriter> et <xref:System.IO.BinaryReader?displayProperty=fullName> sont utilisées pour écrire et lire des données plutôt que des chaînes de caractères.  L'exemple de code suivant montre comment écrire et lire les données dans un nouveau flux de fichier vide `Test.data`.  Après la création du fichier de données dans le répertoire actif, les objets associés <xref:System.IO.BinaryWriter> et <xref:System.IO.BinaryReader> sont créés, et l'objet <xref:System.IO.BinaryWriter> est utilisé pour écrire les entiers de 0 à 10 dans `Test.data`, ce qui laisse le pointeur de fichier à la fin du fichier.  Après avoir repositionné le pointeur de fichier à son emplacement initial, l'objet <xref:System.IO.BinaryReader> lit le contenu spécifié.  
  
## Exemple  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## Programmation fiable  
 Si `Test.data` existe déjà dans le répertoire actif, une exception <xref:System.IO.IOException> est levée.  Utilisez l'option de mode d'accès au fichier <xref:System.IO.FileMode?displayProperty=fullName> lorsque vous initialisez le flux de fichiers afin de toujours créer un fichier sans lever d'exception.  
  
## Voir aussi  
 <xref:System.IO.BinaryReader>   
 <xref:System.IO.BinaryWriter>   
 <xref:System.IO.FileStream>   
 <xref:System.IO.FileStream.Seek%2A?displayProperty=fullName>   
 <xref:System.IO.SeekOrigin>   
 [Comment : énumérer des répertoires et des fichiers](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)   
 [Comment : ouvrir un fichier journal et y ajouter des éléments](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)   
 [Comment : lire du texte dans un fichier](../../../docs/standard/io/how-to-read-text-from-a-file.md)   
 [Comment : écrire du texte dans un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)   
 [Comment : lire les caractères d'une chaîne](../../../docs/standard/io/how-to-read-characters-from-a-string.md)   
 [Comment : écrire des caractères dans une chaîne](../../../docs/standard/io/how-to-write-characters-to-a-string.md)   
 [Fichier et flux de données E\/S](../../../docs/standard/io/index.md)