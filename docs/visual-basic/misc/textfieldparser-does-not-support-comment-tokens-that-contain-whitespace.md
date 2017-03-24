---
title: "TextFieldParser ne prend pas en charge les jetons de commentaires qui contiennent un blanc | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrTextFieldParser_WhitespaceInToken"
ms.assetid: 55107656-270e-4bbb-841a-478904df8e07
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# TextFieldParser ne prend pas en charge les jetons de commentaires qui contiennent un blanc
Un jeton de commentaire qui contient un espace blanc a été fourni.`TextFieldParser` ne prend pas en charge les jetons de commentaires qui contiennent un espace blanc, sauf si ce dernier se trouve au début du jeton. Un espace blanc situé au début d’un jeton est ignoré.  
  
### Pour corriger cette erreur  
  
-   Fournissez un jeton de commentaire correct.  
  
## Voir aussi  
 [TextFieldParser.CommentTokens, propriété](http://msdn.microsoft.com/fr-fr/2e6b6435-4bee-4c14-a353-e8f2c82e2d61)   
 [Parsing Text Files with the TextFieldParser Object](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)   
 [TextFieldParser Object](../../visual-basic/language-reference/objects/textfieldparser-object.md)