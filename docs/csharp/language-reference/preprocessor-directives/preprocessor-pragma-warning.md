---
title: "#pragma warning (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "#pragma warning"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#pragma warning (C#)"
ms.assetid: 723493d5-9753-4cec-babb-54e2b8eb36b6
caps.latest.revision: 17
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #pragma warning (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#pragma warning` peut activer ou désactiver certains avertissements.  
  
## Syntaxe  
  
```  
#pragma warning disable warning-list  
#pragma warning restore warning-list  
```  
  
#### Paramètres  
 `warning-list`  
 Liste de numéros d'avertissement séparés par des virgules.  Entrez les nombres seuls, sans le préfixe "CS".  
  
 Lorsque aucun numéro d'avertissement n'est spécifié, `disable` désactive tous les avertissements et `restore` les active tous.  
  
> [!NOTE]
>  Pour trouver des numéros d'avertissement dans Visual Studio, générez votre projet, puis recherchez les numéros d'avertissement dans la fenêtre **Sortie**.  
  
## Exemple  
  
```  
// pragma_warning.cs  
using System;  
  
#pragma warning disable 414, 3021  
[CLSCompliant(false)]  
public class C  
{  
    int i = 1;  
    static void Main()  
    {  
    }  
}  
#pragma warning restore 3021  
[CLSCompliant(false)]  // CS3021  
public class D  
{  
    int i = 1;  
    public static void F()  
    {  
    }  
}  
```  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C\#](../../../csharp/language-reference/preprocessor-directives/index.md)   
 [C\# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md)