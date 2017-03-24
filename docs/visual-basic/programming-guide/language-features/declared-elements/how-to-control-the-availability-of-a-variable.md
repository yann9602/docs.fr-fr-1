---
title: "How to: Control the Availability of a Variable (Visual Basic) | Microsoft Docs"
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
  - "access levels, declared elements"
  - "Private keyword, accessing variables"
  - "access levels, variables"
  - "Public keyword, accessing variables"
  - "Friend keyword, accessing variables"
  - "variables [Visual Basic], access level"
  - "declared elements, access level"
  - "Protected keyword, accessing variables"
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Control the Availability of a Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez contrôler la disponibilité d'une variable en spécifiant son *niveau d'accès*.  Le niveau d'accès détermine quel code a l'autorisation de lire ou d'écrire dans la variable.  
  
-   Les *variables membres* \(définies au niveau du module et en dehors de toute procédure\) autorisent par défaut un accès public, ce qui signifie que tout code peut les consulter et y accéder.  Vous pouvez modifier cela en spécifiant un modificateur d'accès.  
  
-   Les *variables locales* \(définies à l'intérieur d'une procédure\) ont un accès public nominativement, bien que seul le code situé dans leur procédure puisse y accéder.  Vous ne pouvez pas modifier le niveau d'accès d'une variable locale, mais vous pouvez modifier celui de la procédure qui la contient.  
  
 Pour plus d'informations, consultez [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Accès privé et public  
  
#### Pour rendre une variable accessible uniquement à partir de son module, de sa classe ou de sa structure  
  
1.  Placez l'[Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) pour la variable à l'intérieur du module, de la classe ou de la structure, mais en dehors de toute procédure.  
  
2.  Incluez le mot clé [Private](../../../../visual-basic/language-reference/modifiers/private.md) dans l'instruction `Dim`.  
  
     Vous pouvez lire ou écrire dans la variable à partir de tout emplacement dans le module, la classe ou la structure, mais pas depuis l'extérieur.  
  
#### Pour rendre une variable accessible à partir de tout code qui peut le consulter  
  
1.  Pour une variable membre, placez l'instruction `Dim` pour la variable à l'intérieur d'un module, d'une classe ou d'une structure, mais en dehors de toute procédure.  
  
2.  Incluez le mot clé [Public](../../../../visual-basic/language-reference/modifiers/public.md) dans l'instruction `Dim`.  
  
     Vous pouvez lire ou écrire dans la variable à partir de tout code qui interagit avec votre assembly.  
  
 ou  
  
1.  Pour une variable locale, placez l'instruction `Dim` pour la variable à l'intérieur d'une procédure.  
  
2.  N'incluez pas le mot clé `Public` dans l'instruction `Dim`.  
  
     Vous pouvez lire ou écrire dans la variable à partir de tout emplacement dans la procédure, mais pas depuis l'extérieur.  
  
## Accès protégé et ami  
 Vous pouvez limiter le niveau d'accès d'une variable à sa classe et à toute classe dérivée, ou à son assembly.  Vous pouvez spécifier également l'union de ces limitations, ce qui autorise l'accès à partir de code situé dans toute classe dérivée ou à tout autre emplacement dans le même assembly.  Vous spécifiez cette union en combinant les mots clé `Protected` et `Friend` dans la même déclaration.  
  
#### Pour rendre une variable accessible uniquement à partir de sa classe et de toute classe dérivée  
  
1.  Placez l'instruction `Dim` pour la variable à l'intérieur d'une classe, mais en dehors de toute procédure.  
  
2.  Incluez le mot clé [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) dans l'instruction `Dim`.  
  
     Vous pouvez lire ou écrire dans la variable à partir de tout emplacement dans la classe, ainsi que depuis toute classe dérivée d'elle, mais pas depuis l'extérieur d'une classe dans la chaîne de dérivation.  
  
#### Pour rendre une variable accessible uniquement à partir du même assembly  
  
1.  Placez l'instruction `Dim` pour la variable à l'intérieur d'un module, d'une classe ou d'une la structure, mais en dehors de toute procédure.  
  
2.  Incluez le mot clé [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) dans l'instruction `Dim`.  
  
     Vous pouvez lire ou écrire dans la variable à partir de tout emplacement dans le module, la classe ou la structure, ainsi qu'à partir de tout code situé dans le même assembly, mais pas depuis l'extérieur de l'assembly.  
  
## Exemple  
 L'exemple suivant montre des déclarations de variables avec des niveaux d'accès `Public`, `Protected`, `Friend`, `Protected Friend` et `Private`.  Notez que lorsque l'instruction `Dim` spécifie un niveau d'accès, il n'est pas nécessaire d'inclure le mot clé `Dim`.  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## Sécurité .NET Framework  
 Plus le niveau d'accès d'une variable est restrictif, moins il y a de risques que du code malveillant en fasse une utilisation incorrecte.  
  
## Voir aussi  
 [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)   
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Public](../../../../visual-basic/language-reference/modifiers/public.md)   
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)   
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)   
 [Private](../../../../visual-basic/language-reference/modifiers/private.md)