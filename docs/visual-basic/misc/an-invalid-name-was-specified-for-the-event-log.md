---
title: "Un nom de fichier non valide a &#233;t&#233; sp&#233;cifi&#233; pour le journal des &#233;v&#233;nements | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Un nom de fichier non valide a &#233;t&#233; sp&#233;cifi&#233; pour le journal des &#233;v&#233;nements
Un nom de fichier non valide a été spécifié pour le journal des événements. Cette erreur est généralement due à des caractères non valides dans le nom, à un nom de fichier vide ou à un nom de fichier trop long.  
  
### Pour corriger cette erreur  
  
-   Si le nom spécifié fait plus de huit caractères, vérifiez qu’il n’existe aucun conflit avec les noms des autres journaux des événements. Seuls les huit premiers caractères sont évalués pour déterminer si le nom est unique.  
  
-   Si vous fournissez un chemin, vérifiez qu’il est correctement analysé.  
  
-   Vérifiez que le nom ne contient aucun caractère non valide. Les caractères `<`, `>`, `:`, `"`, `/`, `\` et `|` ne peuvent pas être utilisés dans un nom de fichier.  
  
## Voir aussi  
 [Comment : analyser des chemins d'accès](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)   
 [How to: Rename a File](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)   
 [How to: Create and Remove Custom Event Logs](http://msdn.microsoft.com/fr-fr/af9b7da0-80c7-46ac-b7f7-897063ddd503)