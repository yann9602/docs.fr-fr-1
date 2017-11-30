---
title: "Comment : écrire des caractères dans une chaîne"
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
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 336a7fec5e64cc0c45566631c73928e0c1d40a5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-characters-to-a-string"></a>Comment : écrire des caractères dans une chaîne
Les exemples de code suivants écrivent des caractères de façon synchrone et asynchrone à partir d’un tableau de caractères en une chaîne.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant écrit 5 caractères de façon synchrone à partir d’un tableau, en une chaîne.  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant lit tous les caractères de façon asynchrone un <xref:System.Windows.Controls.TextBox> de contrôle et les stocke dans un tableau. Il puis écrit de façon asynchrone chaque caractère lettre ou un espace blanc sur une ligne distincte, suivie d’un saut de ligne à un <xref:System.Windows.Controls.TextBlock> contrôle.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.StringWriter>  
 <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
 <xref:System.Text.StringBuilder>  
 [Fichier et flux de données E/S](../../../docs/standard/io/index.md)  
 [E/S sur fichier asynchrones](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [Guide pratique pour énumérer des répertoires et des fichiers](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Comment : lire et écrire dans un fichier de données créé récemment](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Comment : ouvrir un fichier journal et y ajouter des éléments](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [Comment : lire du texte dans un fichier](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Comment : écrire du texte dans un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Comment : lire les caractères d’une chaîne](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
