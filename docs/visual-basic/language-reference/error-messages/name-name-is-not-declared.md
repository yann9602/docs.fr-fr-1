---
title: "Name &#39;&lt;name&gt;&#39; is not declared | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30451"
  - "vbc30451"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30451"
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Name &#39;&lt;name&gt;&#39; is not declared
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une instruction fait référence à un élément de programmation, mais le compilateur ne peut pas trouver d'élément avec ce nom exact.  
  
 **ID d'erreur :** BC30451  
  
### Pour corriger cette erreur  
  
1.  Vérifiez l'orthographe du nom dans l'instruction faisant référence.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] n'est pas sensible à la casse, mais toute autre variation dans l'orthographe est considérée comme un nom complètement différent.  Notez que le trait de soulignement \(`_`\) fait partie du nom et, par conséquent, de l'orthographe.  
  
2.  Vérifiez que vous avez l'opérateur d'accès au membre \(`.`\) entre un objet et son membre.  Par exemple, si vous avez un contrôle <xref:System.Windows.Forms.TextBox> nommé `TextBox1`, vous devez, pour accéder à sa propriété <xref:System.Windows.Forms.TextBoxBase.Text%2A>, taper `TextBox1.Text`.  Si, au lieu de cela, vous tapez `TextBox1Text`, vous avez créé un nom différent.  
  
3.  Si l'orthographe est correcte et que la syntaxe de l'accès au membre objet est correcte, vérifiez que l'élément a été déclaré.  Pour plus d'informations, consultez [Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).  
  
4.  Si l'élément de programmation a été déclaré, vérifiez qu'il est dans la portée.  Si l'instruction de référence se trouve à l'extérieur de la région qui déclare l'élément de programmation, vous devrez peut\-être qualifier le nom d'élément.  Pour plus d'informations, consultez [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## Voir aussi  
 [Declarations and Constants Summary](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)