---
title: "L'entrée dépasse la fin du fichier"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 27de462d5d28ee09107d75afe8269e7401c4dc39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="input-past-end-of-file"></a>L'entrée dépasse la fin du fichier
Soit un `Input` instruction lit à partir d’un fichier qui est vide ou dans lequel toutes les données est utilisée, ou vous avez utilisé le `EOF` fonction avec un fichier ouvert pour un accès binaire.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Utilisez le `EOF` de fonction immédiatement avant la `Input` instruction pour détecter la fin du fichier.  
  
2.  Si le fichier est ouvert pour un accès binaire, utilisez `Seek` et `Loc`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileSystem.Input%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
