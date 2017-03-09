---
title: "Absence de souris | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrMouse_NoMouseIsPresent"
ms.assetid: 4472fd57-4217-4463-9d3c-dc4a8fe88f1b
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Absence de souris
L’une des propriétés de l’objet `My.Computer.Mouse` a été appelée, mais aucune souris ou aucun port de souris n’est installé sur l’ordinateur.  
  
### Pour corriger cette erreur  
  
-   Ajoutez un bloc `Try...Catch` autour de l’appel à la propriété de l’objet `My.Computer.Mouse`.  
  
     — ou —  
  
-   Installez une souris sur l’ordinateur.  
  
## Voir aussi  
 [My.Computer.Mouse Object](../../visual-basic/language-reference/objects/my-computer-mouse-object.md)   
 [Gestion des exceptions et des erreurs en Visual Basic](http://msdn.microsoft.com/fr-fr/3e351e73-cf23-40ab-8b60-05794160529e)   
 [Try...Catch...Finally Statement](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)