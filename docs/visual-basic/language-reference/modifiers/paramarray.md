---
title: "ParamArray (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ParamArray"
  - "ParamArray"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ParamArray keyword"
  - "ParamArray keyword, syntax"
ms.assetid: a5f18789-92bd-488f-9c7e-cf3719963635
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ParamArray (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie qu'un paramètre de procédure prend un tableau facultatif d'éléments du type spécifié.  `ParamArray` peut être utilisé uniquement sur le dernier paramètre d'une liste de paramètres.  
  
## Notes  
 `ParamArray` vous permet de passer à la procédure un nombre arbitraire d'arguments.  Un paramètre `ParamArray` est toujours déclaré à l'aide de [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).  
  
 Vous pouvez fournir un ou plusieurs arguments à un paramètre `ParamArray` en passant un tableau du type de données approprié, une liste avec la virgule comme séparateur de valeurs, ou rien du tout.  Pour plus d'informations, consultez la section « Appel d'un ParamArray » de la rubrique [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).  
  
> [!IMPORTANT]
>  Si vous travaillez dans un tableau dont la taille peut être indéfinie, vous risquez de saturer la capacité interne de votre application.  Si vous acceptez un tableau de paramètres à partir du code appelant, vous devez tester sa longueur et prendre des mesures appropriées s'il est trop grand pour votre application.  
  
 Le modificateur `ParamArray` peut être utilisé dans les contextes suivants :  
  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Voir aussi  
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)   
 [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)