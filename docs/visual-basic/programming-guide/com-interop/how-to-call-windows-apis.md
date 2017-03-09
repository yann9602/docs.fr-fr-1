---
title: "How to: Call Windows APIs (Visual Basic) | Microsoft Docs"
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
  - "API calls"
  - "Windows API, calling"
  - "API calls, platform invoke"
  - "calls, stored procedures"
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Call Windows APIs (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Cet exemple définit et appelle la fonction `MessageBox` dans user32.dll et lui passe une chaîne.  
  
## Exemple  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#1)]  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Référence à l'espace de noms <xref:System>.  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   La méthode n'est pas statique, elle est abstraite ou a été définie précédemment.  Le type parent est une interface, ou la longueur de *name* ou *dllName* est zéro.  \(<xref:System.ArgumentException>\)  
  
-   Le *name* ou *dllName* est `Nothing`.  \(<xref:System.ArgumentNullException>\)  
  
-   Le type conteneur a été créé précédemment à l'aide de `CreateType`.  \(<xref:System.InvalidOperationException>\)  
  
## Voir aussi  
 [A Closer Look at Platform Invoke](http://msdn.microsoft.com/fr-fr/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)   
 [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md)   
 [Consuming Unmanaged DLL Functions](../Topic/Consuming%20Unmanaged%20DLL%20Functions.md)   
 [Defining a Method with Reflection Emit](http://msdn.microsoft.com/fr-fr/84fd3bf6-628f-41aa-83d9-b990cf926e81)   
 [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)