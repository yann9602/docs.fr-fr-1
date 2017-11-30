---
title: Le codage ne peut pas avoir la valeur Nothing
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 59f7c731-8291-4a85-bf51-c225e48cdc84
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa3567e47f170c64b45cbb9e49d7fa0026b8903
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="encoding-cannot-be-set-to-nothing"></a>Le codage ne peut pas avoir la valeur Nothing
Une tentative de lecture ou d’écriture dans un fichier a échoué, car le paramètre `encoding` a la valeur `Nothing` , mais requiert une valeur valide.  
  
 <xref:System.Text.Encoding> est utilisé pour déterminer le codage à utiliser lors de l’écriture dans un fichier. La valeur par défaut est UTF-8.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Fournissez une valeur valide pour le paramètre `encoding` .  
  
## <a name="see-also"></a>Voir aussi  
 [Codages de fichiers](../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 [Lecture à partir de fichiers](../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [Écriture dans des fichiers](../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [My.Computer.FileSystem.ReadAllText, méthode](http://msdn.microsoft.com/en-us/3a7ac8be-fb1d-4087-bc65-167d6754d57f)  
 [My.Computer.FileSystem.WriteAllText (méthode)](http://msdn.microsoft.com/en-us/f507460c-87d9-4504-b74f-3ff825c7d5c4)
