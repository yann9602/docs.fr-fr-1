---
title: "#region (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#region"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#region (directive C#)"
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #region (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#region` vous permet de spécifier un bloc de code que vous pouvez développer ou réduire lors de l'utilisation de la fonctionnalité [Mode Plan](/visual-studio/ide/outlining) de l'éditeur de code de Visual Studio.  Dans les plus longs fichiers de code, il est commode de pouvoir réduire ou masquer une ou plusieurs régions afin de vous concentrer sur la partie du fichier sur laquelle vous êtes en train de travailler.  L'exemple suivant montre comment définir une région :  
  
```  
  
      #region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## Notes  
 Un bloc `#region` doit se terminer par une directive [\#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md).  
  
 Un bloc `#region` ne peut pas se superposer à un bloc [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).  Toutefois, un bloc `#region` peut être imbriqué dans un bloc `#if` et un bloc `#if` peut être imbriqué dans un bloc `#region`.  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C\#](../../../csharp/language-reference/preprocessor-directives/index.md)