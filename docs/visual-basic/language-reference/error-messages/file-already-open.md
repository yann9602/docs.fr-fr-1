---
title: "Le fichier est déjà ouvert."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID55
ms.assetid: d674a0fb-ef16-4cc2-9da7-709a8a07dbea
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3305831e840510e3f0b5bcb8bf847e39ea3ee4ba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="file-already-open"></a>Le fichier est déjà ouvert.
Un fichier doit parfois être fermé avant un autre `FileOpen` ou autre opération ne peut se produire. Cette erreur peut avoir plusieurs causes, dont les suivantes :  
  
-   Un mode de sortie séquentielle `FileOpen` opération a été exécutée pour un fichier qui est déjà ouvert  
  
-   Une instruction fait référence à un fichier ouvert.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Fermez le fichier avant d’exécuter l’instruction.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>
