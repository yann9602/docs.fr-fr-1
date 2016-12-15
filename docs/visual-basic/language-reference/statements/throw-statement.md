---
title: "Throw Statement (Visual Basic) | Microsoft Docs"
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
  - "vb.Throw"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "structured exception handling, throw statements"
  - "try-catch exception handling, throw statements"
  - "throw statement, about throw statements"
  - "throwing exceptions, throw statement"
  - "exception handling, throw statement"
  - "On Error statement, throwing exceptions"
  - "throwing exceptions"
  - "exception handling, unstructured"
  - "throw statement"
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Throw Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Lève une exception dans une procédure.  
  
## Syntaxe  
  
```  
Throw [ expression ]  
```  
  
## Élément  
 `expression`  
 Fournit des informations sur l'exception à lever.  Facultatif lorsqu'elle est présente dans une instruction `Catch`, sinon obligatoire.  
  
## Notes  
 L'instruction `Throw` lève une exception que vous pouvez gérer à l'aide du code de gestion structurée des exceptions \(`Try`...`Catch`...`Finally`\) ou du code de gestion non structurée des exceptions \(`On Error GoTo`\).  Vous pouvez utiliser l'instruction `Throw` pour intercepter les erreurs dans votre code, compte tenu que Visual Basic monte dans la pile des appels jusqu'à ce qu'il trouve le code de gestion des exceptions approprié.  
  
 Une instruction `Throw` sans expression peut être utilisée uniquement dans une instruction `Catch`, auquel cas elle lève de nouveau l'exception qui est gérée par l'instruction `Catch`.  
  
 L'instruction `Throw` réinitialise la pile d'appel pour l'exception `expression`.  Si `expression` n'est pas fournie, la pile d'appel demeure inchangée.  Vous pouvez accéder à la pile d'appel pour l'exception à travers la propriété <xref:System.Exception.StackTrace%2A>.  
  
## Exemple  
 Le code suivant utilise l'instruction `Throw` pour lever une exception :  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## Configuration requise  
 **Espace de noms :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **Module :** `Interaction`  
  
 **Assembly :** bibliothèque Runtime Visual Basic \(dans Microsoft.VisualBasic.dll\)  
  
## Voir aussi  
 [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)