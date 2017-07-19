---
title: "Comment&#160;: ouvrir un fichier journal et y ajouter des &#233;l&#233;ments | Microsoft Docs"
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
  - "fichiers journaux, ouverture"
  - "flux, ouverture et ajout à un fichier journal"
  - "fichiers journaux, ajout"
  - "E/S (.NET Framework), fichiers journaux"
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: ouvrir un fichier journal et y ajouter des &#233;l&#233;ments
Les objets <xref:System.IO.StreamWriter> et <xref:System.IO.StreamReader> lisent des caractères à partir des flux ou les y écrivent.  L'exemple de code suivant ouvre le fichier `log.txt` en entrée, ou crée le fichier s'il n'existe pas déjà, et ajoute les informations en fin de fichier.  Le contenu du fichier est ensuite écrit dans une sortie standard pour être affiché.  Une autre solution consisterait à stocker les informations en tant que chaîne unique ou tableau de chaînes et à utiliser la méthode <xref:System.IO.File.WriteAllText%2A> ou <xref:System.IO.File.WriteAllLines%2A> pour obtenir les mêmes fonctionnalités.  
  
> [!NOTE]
>  Les utilisateurs de Visual Basic peuvent choisir d'utiliser les méthodes et les propriétés fournies par les classes <xref:Microsoft.VisualBasic.Logging.Log> ou <xref:Microsoft.VisualBasic.FileIO.FileSystem> pour les E\/S de fichiers.  
  
## Exemple  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## Voir aussi  
 <xref:System.IO.StreamWriter>   
 <xref:System.IO.StreamReader>   
 <xref:System.IO.File.AppendText%2A?displayProperty=fullName>   
 <xref:System.IO.File.OpenText%2A?displayProperty=fullName>   
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName>   
 [Comment : énumérer des répertoires et des fichiers](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)   
 [Comment : lire et écrire dans un fichier de données créé récemment](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)   
 [Comment : lire du texte dans un fichier](../../../docs/standard/io/how-to-read-text-from-a-file.md)   
 [Comment : écrire du texte dans un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)   
 [Comment : lire les caractères d'une chaîne](../../../docs/standard/io/how-to-read-characters-from-a-string.md)   
 [Comment : écrire des caractères dans une chaîne](../../../docs/standard/io/how-to-write-characters-to-a-string.md)   
 [Fichier et flux de données E\/S](../../../docs/standard/io/index.md)