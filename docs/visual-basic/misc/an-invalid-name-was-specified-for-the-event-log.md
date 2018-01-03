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
ms.openlocfilehash: 76e4082710a6786ec5e743ce606e849637c26512
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
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
 
