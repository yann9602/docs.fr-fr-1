---
title: "Comment&#160;: &#233;crire des caract&#232;res dans une cha&#238;ne | Microsoft Docs"
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
  - "flux de données, écrire des caractères dans une chaîne"
  - "écrire des caractères dans des chaînes"
  - "flux, écrire des caractères dans des chaînes"
  - "E/S (.NET Framework), écrire des caractères dans des chaînes"
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
caps.latest.revision: 17
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: &#233;crire des caract&#232;res dans une cha&#238;ne
Les exemples de code suivants écrivent des caractères de façon synchrone et asynchrone d'un tableau de caractères en une chaîne.  
  
## Exemple  
 The following example writes 5 characters synchronously from an array to a string.  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## Exemple  
 L'exemple suivant lit tous les caractères asynchrone d'un contrôle <xref:System.Windows.Controls.TextBox>, et les stocke dans un tableau.  Il écrit ensuite de manière asynchrone chaque caractères ou espace blanc sur une ligne distincte suivi d'un saut de ligne à un contrôle <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## Voir aussi  
 <xref:System.IO.StringWriter>   
 <xref:System.IO.StringWriter.Write%2A?displayProperty=fullName>   
 <xref:System.Text.StringBuilder>   
 [Fichier et flux de données E\/S](../../../docs/standard/io/index.md)   
 [E\/S sur fichier asynchrones](../../../docs/standard/io/e-s-sur-fichier-asynchrones.md)   
 [Comment : énumérer des répertoires et des fichiers](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)   
 [Comment : lire et écrire dans un fichier de données créé récemment](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)   
 [Comment : ouvrir un fichier journal et y ajouter des éléments](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)   
 [Comment : lire du texte dans un fichier](../../../docs/standard/io/how-to-read-text-from-a-file.md)   
 [Comment : écrire du texte dans un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)   
 [Comment : lire les caractères d'une chaîne](../../../docs/standard/io/how-to-read-characters-from-a-string.md)