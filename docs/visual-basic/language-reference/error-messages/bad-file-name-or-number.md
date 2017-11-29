---
title: "Nom ou numéro de fichier incorrect"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-name-or-number"></a>Nom ou numéro de fichier incorrect
Une erreur s’est produite lors de la tentative d’accès au fichier spécifié. Parmi les causes possibles de cette erreur sont :  
  
-   Une instruction fait référence à un fichier avec un nom de fichier ou d’un nombre qui n’a pas été spécifié dans le `FileOpen` instruction ou qui a été spécifié dans un `FileOpen` instruction mais a ensuite fermé.  
  
-   Une instruction fait référence à un fichier avec un nombre qui est en dehors de la plage des numéros de fichier.  
  
-   Une instruction fait référence à un nom de fichier ou un nombre qui n’est pas valide.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Assurez-vous que le nom de fichier est spécifié dans un `FileOpen` instruction. Notez que si vous avez appelé la `FileClose` instruction sans arguments, vous avez peut-être fermé accidentellement tous les fichiers ouverts.  
  
2.  Si votre code génère des nombres de fichier par algorithme, vérifiez que les nombres sont valides.  
  
3.  Vérifiez les noms de fichiers pour vous assurer qu’elles sont conformes aux conventions du système d’exploitation.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
