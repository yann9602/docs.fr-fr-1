---
title: "Directives (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "directives, Visual Basic compiler"
  - "Visual Basic code, directives"
  - "directives"
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Directives (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Les rubriques de cette section documentent les directives du compilateur de code source Visual Basic.  
  
## Dans cette section  
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) : définir une constante de compilation  
  
 [\#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) : indiquer un mappage entre des lignes sources et du texte externe à la source  
  
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) : compiler des blocs de code sélectionnés  
  
 [\#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) : réduire et masquer des sections de code dans l'éditeur Visual Studio  
  
 **\#Disable, \#Enable** : désactiver et activer des avertissements spécifiques pour des régions de code.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
  
```  
  
 Vous pouvez désactiver et activer une liste séparée par des virgules de codes d'avertissement.  
  
## Rubriques connexes  
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)