---
title: "NumberOfChars doit &#234;tre sup&#233;rieur &#224; z&#233;ro | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrTextFieldParser_NumberOfCharsMustBePositive"
ms.assetid: 3eea4bbf-cd49-4d19-adfb-0e2adf087065
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# NumberOfChars doit &#234;tre sup&#233;rieur &#224; z&#233;ro
Quand vous utilisez la méthode `PeekChars` de l’objet `TextFieldParser`, vous devez fournir une valeur `NumberOfChars` supérieure à `0`.  
  
### Pour corriger cette erreur  
  
-   Remplacez `NumberOfChars` par une valeur supérieure à `0`.  
  
## Voir aussi  
 [How to: Read From Text Files with Multiple Formats](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [My.Computer.FileSystem.OpenTextFieldParser, méthode](http://msdn.microsoft.com/fr-fr/e5869f85-c078-485f-8323-8dc716494546)   
 [TextFieldParser.PeekChars, méthode](http://msdn.microsoft.com/fr-fr/4a180d26-d46d-4cc1-9af7-d23abe27c89b)   
 [Parsing Text Files with the TextFieldParser Object](../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)   
 [TextFieldParser Object](../../visual-basic/language-reference/objects/textfieldparser-object.md)