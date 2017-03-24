---
title: "Default (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Default"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "defaults, properties"
  - "properties [Visual Basic], default"
  - "default properties, in Visual Basic"
  - "Default keyword [Visual Basic]"
  - "default properties"
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Default (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Identifie une propriété comme propriété par défaut de sa classe, structure ou interface.  
  
## Notes  
 Une classe, structure ou interface peut désigner au plus l'une de ses propriétés comme *propriété par défaut*, à condition que la propriété prenne au moins un paramètre.  Si le code fait une référence à une classe ou structure sans spécifier un membre, Visual Basic résout cette référence à la propriété par défaut.  
  
 Les propriétés par défaut peuvent entraîner une légère réduction des caractères de code source, mais elles peuvent rendre votre code plus difficile à lire.  Si le code appelant ne connaît pas votre classe ou votre structure, lorsqu'il fait référence au nom de la classe ou de la structure, il ne peut pas déterminer avec certitude si cette référence accède à la classe ou à la structure elle\-même ou à une propriété par défaut.  Cela peut engendrer des erreurs du compilateur ou des erreurs de logique d'exécution subtiles.  
  
 Vous pouvez légèrement réduire la probabilité que se produisent des erreurs de propriété par défaut en utilisant toujours l'[Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) pour affecter la valeur `On` au contrôle de type de compilateur.  
  
 Si vous envisagez d'utiliser une classe ou une structure prédéfinie dans votre code, vous devez déterminer si elle a une propriété par défaut, et, le cas échéant, indiquer son nom.  
  
 À cause de ces inconvénients, vous devez envisager de ne pas définir de propriétés par défaut.  Afin de garantir la lisibilité du code, vous devez également envisager de toujours faire référence explicitement à toutes les propriétés, y compris aux propriétés par défaut.  
  
 Le modificateur `Default` peut être utilisé dans le contexte suivant :  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## Voir aussi  
 [How to: Declare and Call a Default Property in Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)