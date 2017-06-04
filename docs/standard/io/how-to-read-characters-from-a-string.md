---
title: "Comment&#160;: lire les caract&#232;res d&#39;une cha&#238;ne | Microsoft Docs"
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
  - "lire des caractères dans des chaînes"
  - "flux de données, lire les caractères d’une chaîne"
  - "E/S (.NET Framework), lire des caractères dans des chaînes"
  - "lire des données, chaînes"
  - "flux, lire les caractères d’une chaîne"
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: lire les caract&#232;res d&#39;une cha&#238;ne
Les exemples de code suivants montrent comment lire des caractères de façon synchrone et asynchrone d'une chaîne.  
  
## Exemple  
 Cet exemple lit 13 caractères de façon synchrone d'une chaîne, les stocke dans un tableau, et affiche ces caractères.  Il lit les autres dans la chaîne, les stocke dans le tableau à partir du sixième élément, et présente le contenu du tableau.  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## Exemple  
 L'exemple suivant lit tous les caractères asynchrone d'un contrôle <xref:System.Windows.Controls.TextBox>, et les stocke dans un tableau.  Il écrit ensuite de manière asynchrone chaque caractères ou espace blanc sur une ligne distincte suivi d'un saut de ligne à un contrôle <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## Voir aussi  
 <xref:System.IO.StringReader>   
 <xref:System.IO.StringReader.Read%2A?displayProperty=fullName>   
 [E\/S sur fichier asynchrones](../../../docs/standard/io/e-s-sur-fichier-asynchrones.md)   
 [NIB: How to: Create a Directory Listing](http://msdn.microsoft.com/fr-fr/4d2772b1-b991-4532-a8a6-6ef733277e69)   
 [Comment : lire et écrire dans un fichier de données créé récemment](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)   
 [Comment : ouvrir un fichier journal et y ajouter des éléments](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)   
 [Comment : lire du texte dans un fichier](../../../docs/standard/io/how-to-read-text-from-a-file.md)   
 [Comment : écrire du texte dans un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)   
 [Comment : écrire des caractères dans une chaîne](../../../docs/standard/io/how-to-write-characters-to-a-string.md)   
 [Fichier et flux de données E\/S](../../../docs/standard/io/index.md)