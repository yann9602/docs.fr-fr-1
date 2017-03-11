---
title: "How to: Collapse and Hide Sections of Code (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic, code collapsing"
  - "Visual Basic, code hiding"
  - "Visual Basic code, collapsing and hiding"
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Collapse and Hide Sections of Code (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

La directive `#Region` vous permet de réduire et de masquer des sections de code dans des fichiers [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  La directive `#Region` vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lorsque vous utilisez l'éditeur de code [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)].  Cette fonctionnalité de masquage sélectif du code facilite la gestion et la lecture de vos fichiers.  Pour plus d'informations, consultez [Mode Plan](/visual-studio/ide/outlining).  
  
 Les directives `#Region` prennent en charge la sémantique de bloc de code telle que `#If...#End If`.  Elles ne peuvent donc pas commencer dans un bloc et se terminer dans un autre ; le début et la fin d'une directive doivent figurer dans le même bloc.  Les directives `#Region` ne sont pas prises en charge dans les fonctions.  
  
### Pour réduire et masquer une section de code  
  
-   Placez la section de code entre les instructions `#Region` et `#End Region`, comme dans l'exemple suivant :  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/visualbasic/how-to-collapse-and-hide_1.vb)]  
  
     Le bloc `#Region` peut être utilisé plusieurs fois dans un fichier de code ; par conséquent, les utilisateurs ont la possibilité de définir leurs propres blocs de procédures et classes qui peuvent, à leur tour, être réduits.  Les blocs `#Region` peuvent également être imbriqués dans d'autres blocs `#Region`.  
  
    > [!NOTE]
    >  Le masquage du code n'empêche pas sa compilation et n'affecte pas les instructions `#If...#End If`.  
  
## Voir aussi  
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [\#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md)   
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Mode Plan](/visual-studio/ide/outlining)