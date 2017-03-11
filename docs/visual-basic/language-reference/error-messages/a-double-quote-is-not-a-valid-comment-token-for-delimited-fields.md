---
title: "Les guillemets doubles ne constituent pas un jeton de commentaire valide pour les champs d&#233;limit&#233;s quand EscapeQuote a la valeur True | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrTextFieldParser_InvalidComment"
dev_langs: 
  - "VB"
ms.assetid: 636d4b81-00ba-4cfd-98f7-4d57036f494d
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Les guillemets doubles ne constituent pas un jeton de commentaire valide pour les champs d&#233;limit&#233;s quand EscapeQuote a la valeur True
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Un guillemet a été fourni comme délimiteur pour `TextFieldParser`, mais `EscapeQuotes` a la valeur `True`.  
  
### Pour corriger cette erreur  
  
-   Affectez la valeur `False` à `EscapeQuotes`.  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>   
 [How to: Read From Comma\-Delimited Text Files](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)