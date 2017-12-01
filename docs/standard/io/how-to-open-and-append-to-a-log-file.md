---
title: "Comment : ouvrir un fichier journal et y ajouter des éléments"
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
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60c31339231405a1cbbb98dae37d36ad3c3709c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Comment : ouvrir un fichier journal et y ajouter des éléments
<xref:System.IO.StreamWriter>et <xref:System.IO.StreamReader> écrire des caractères à et lire des caractères à partir de flux. Le code suivant exemple ouvre le `log.txt` du fichier d’entrée, ou crée le fichier s’il n’existe pas déjà et ajoute les informations à la fin du fichier. Le contenu du fichier est ensuite écrites vers la sortie standard pour l’affichage. Comme alternative à cet exemple, les informations peut être stockées en tant que chaîne unique ou tableau de chaînes et le <xref:System.IO.File.WriteAllText%2A> ou <xref:System.IO.File.WriteAllLines%2A> méthode peut servir à obtenir la même fonctionnalité.  
  
> [!NOTE]
>  Les utilisateurs de Visual Basic peuvent choisir d’utiliser les méthodes et les propriétés fournies par le <xref:Microsoft.VisualBasic.Logging.Log> classe ou <xref:Microsoft.VisualBasic.FileIO.FileSystem> classe pour la création ou l’écriture dans des fichiers journaux.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [Guide pratique pour énumérer des répertoires et des fichiers](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Comment : lire et écrire dans un fichier de données créé récemment](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Comment : lire du texte dans un fichier](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Comment : écrire du texte dans un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Comment : lire les caractères d’une chaîne](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [Comment : écrire des caractères dans une chaîne](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [Fichier et flux de données E/S](../../../docs/standard/io/index.md)
