---
title: "Me, My, MyBase, and MyClass in Visual Basic | Microsoft Docs"
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
  - "MyClass"
  - "vb.Me"
  - "MyBase"
  - "vb.MyBase"
  - "Me"
  - "vb.MyClass"
  - "vb.This"
  - "vb.My"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My object"
  - "self-reference, Me keyword"
  - "MyClass keyword, relationship to similar programming elements"
  - "Me keyword, relationship to similar programming elements"
  - "Me keyword, referring to the current instance of an object"
  - "Me keyword"
  - "self-reference"
  - "current instance, Me keyword"
  - "MyBase keyword, relationship to similar programming elements"
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Me, My, MyBase, and MyClass in Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Me`, `My`, `MyBase` et `MyClass` en [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ont des noms semblables, mais des fonctions différentes.  Cette rubrique décrit chacune de ces entités de façon à les distinguer.  
  
## Me  
 Le mot clé `Me` permet de faire référence à l'instance spécifique d'une classe ou d'une structure dans laquelle le code est en train de s'exécuter.  `Me` se comporte comme une variable objet ou comme une variable de structure faisant référence à l'instance actuelle.  L'utilisation de `Me` est particulièrement utile pour le passage des informations concernant l'instance d'une classe ou d'une structure en cours d'exécution, à une procédure se trouvant dans une autre classe, une autre structure ou un autre module.  
  
 Par exemple, supposons que vous ayez la procédure suivante dans un module.  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 Vous pouvez appeler cette procédure et passer l'instance actuelle de la classe <xref:System.Windows.Forms.Form> en tant qu'argument à l'aide de l'instruction suivante.  
  
```  
ChangeFormColor(Me)  
```  
  
## My  
 La fonction `My` offre un accès facile et intuitif à plusieurs classes du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], ce qui permet à l'utilisateur de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] d'interagir avec l'ordinateur, l'application, les paramètres, les ressources, etc.  
  
## MyBase  
 Le mot clé `MyBase` se comporte comme une variable objet faisant référence à la classe de base de l'instance actuelle d'une classe.  `MyBase` est couramment utilisé pour accéder aux membres de la classe de base qui sont substitués ou occultés dans une classe dérivée.  `MyBase.New` est utilisé pour appeler explicitement un constructeur de classe de base à partir d'un constructeur de classe dérivée.  
  
## MyClass  
 Le mot clé `MyClass` se comporte comme une variable objet faisant référence à l'instance actuelle d'une classe telle qu'elle a été implémentée initialement.  `MyClass` est semblable à `Me`, mais tous les appels de méthode effectués sur celui\-ci sont traités comme si la méthode était `NotOverridable`.  
  
## Voir aussi  
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)