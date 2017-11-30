---
title: "Un nom de fichier non valide a été spécifié pour le journal des événements"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: b1b158bd-f13f-4371-a8af-31c0e86ae6be
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fc5a2e93541063a129efaa0ce08fc19a98372126
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="an-invalid-name-was-specified-for-the-event-log"></a>Un nom de fichier non valide a été spécifié pour le journal des événements
Un nom de fichier non valide a été spécifié pour le journal des événements. Cette erreur est généralement due à des caractères non valides dans le nom, à un nom de fichier vide ou à un nom de fichier trop long.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si le nom spécifié fait plus de huit caractères, vérifiez qu’il n’existe aucun conflit avec les noms des autres journaux des événements. Seuls les huit premiers caractères sont évalués pour déterminer si le nom est unique.  
  
-   Si vous fournissez un chemin, vérifiez qu’il est correctement analysé.  
  
-   Vérifiez que le nom ne contient aucun caractère non valide. Les caractères `<`, `>`, `:`, `"`, `/`, `\`et `|`ne peuvent pas être utilisés dans un nom de fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour analyser des chemins](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)  
 [Guide pratique : renommer un fichier](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [Comment : créer et supprimer des journaux des événements personnalisés](http://msdn.microsoft.com/en-us/af9b7da0-80c7-46ac-b7f7-897063ddd503)
