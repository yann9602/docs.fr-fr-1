---
title: Erreur de chargement de la DLL (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc557dcc6709178b6519adb56f31debcbd1d1c39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="error-in-loading-dll-visual-basic"></a>Erreur de chargement de la DLL (Visual Basic)
Une bibliothèque de liens dynamiques (DLL) est une bibliothèque spécifiée dans la `Lib` clause d’un `Declare` instruction. Les causes possibles de cette erreur sont les suivantes :  
  
-   Le fichier n’est pas exécutable DLL.  
  
-   Le fichier n’est pas une DLL Microsoft Windows.  
  
-   La DLL fait référence à une autre DLL qui n’est pas présente.  
  
-   Le fichier DLL ou la DLL référencée n’est pas un répertoire spécifié dans le chemin d’accès.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si le fichier est un fichier texte source et par conséquent pas un exécutable DLL, il doit être compilé et lié à un formulaire exécutable DLL.  
  
-   Si le fichier n’est pas une DLL Microsoft Windows, obtenir l’équivalent Microsoft Windows.  
  
-   Si la DLL fait référence à une autre DLL qui n’est pas présente, obtenir la DLL référencée et le rendre disponible.  
  
-   Si le fichier DLL ou la DLL référencée n’est pas un répertoire spécifié par le chemin d’accès, déplacez la DLL vers un répertoire référencé.  
  
## <a name="see-also"></a>Voir aussi  
 [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md)
