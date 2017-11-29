---
title: Mode de fichier incorrect
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID54
ms.assetid: 74891e96-884b-4c8d-872d-cd11ae272372
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a540135727eb97f4df5027e2ded7271e21bb4648
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-mode"></a>Mode de fichier incorrect
Les instructions utilisées pour la manipulation du contenu du fichier doivent être adaptées au mode dans lequel le fichier a été ouvert. Plusieurs causes sont possibles :  
  
-   A `FilePutObject` ou `FileGetObject` instruction spécifie un fichier séquentiel.  
  
-   A `Print` instruction spécifie un fichier ouvert pour un mode d’accès autre que `Output` ou `Append`.  
  
-   Un `Input` instruction spécifie un fichier ouvert pour un mode d’accès autre que`Input`  
  
-   Toute tentative d’écriture dans un fichier en lecture seule.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assurez-vous que `FilePutObject` et `FileGetObject` font uniquement référence à des fichiers ouverts pour `Random` ou `Binary` accès.  
  
-   Assurez-vous que `Print` spécifie un fichier ouvert pour un `Output` ou `Append` mode d’accès. Si ce n’est pas le cas, utilisez une instruction différente pour placer des données dans le fichier ou rouvrez le fichier dans un mode approprié.  
  
-   Assurez-vous que `Input` spécifie un fichier ouvert pour `Input`. Si ce n’est pas le cas, utilisez une instruction différente pour placer des données dans le fichier ou rouvrez le fichier dans un mode approprié.  
  
-   Si vous écrivez dans un fichier en lecture seule, de modifier l’état de lecture/écriture du fichier ou n’essayez pas d’écrire dedans.  
  
-   Utilisez les fonctionnalités disponibles dans l’objet `My.Computer.FileSystem` .  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileSystem>  
 [Dépannage : lecture et écriture dans des fichiers texte](../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
