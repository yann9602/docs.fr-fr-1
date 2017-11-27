---
title: Directives (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8219f17f1b8093b4d02b370c7b008101923b1873
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="directives-visual-basic"></a>Directives (Visual Basic)
Les rubriques de cette section documentent les directives du compilateur de code source Visual Basic.  
  
## <a name="in-this-section"></a>Dans cette section  
 [#Const, Directive](../../../visual-basic/language-reference/directives/const-directive.md) --définir une constante de compilation  
  
 [Directive #ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md) --indiquent un mappage entre des lignes sources et du texte externe à la source  
  
 [#If... ... #Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) --compiler des blocs de code sélectionnés  
  
 [Directive #Region](../../../visual-basic/language-reference/directives/region-directive.md) : réduire et masquer des sections de code dans l’éditeur Visual Studio  
  
 **#Disable, #Enable** : désactiver et activer des avertissements spécifiques pour les régions de code.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Vous pouvez désactiver et activer une liste séparée par des virgules de codes d'avertissement.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Informations de référence sur le langage Visual Basic](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)
