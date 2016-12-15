---
title: "Access Levels in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "members, accessing in Visual Basic"
  - "Friend access modifier"
  - "access levels, declared elements"
  - "access levels"
  - "access modifiers"
  - "Public access modifier"
  - "Protected access modifier"
  - "Protected Friend access modifier"
  - "Private access modifier"
  - "declared elements, access level"
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Access Levels in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Le *niveau d'accès* d'un élément déclaré est l'étendue de la capacité à l'utiliser, à savoir le code qui est autorisé à lire l'élément ou à y écrire.  Le niveau d'accès est déterminé d'une part par la façon dont vous déclarez l'élément lui\-même et d'autre part par le niveau d'accès du conteneur de cet élément.  Le code qui ne peut pas accéder à un élément conteneur ne peut accéder à aucun de ses éléments contenus, même qui sont ceux déclarés comme `Public`.  Par exemple, une variable `Public` dans une structure `Private` est accessible à partir de l'intérieur de la classe contenant la structure, mais non à partir de l'extérieur de celle\-ci.  
  
## Public  
 Le mot clé [Public](../../../../visual-basic/language-reference/modifiers/public.md) dans l'instruction de déclaration spécifie que les éléments sont accessibles à partir du code partout à l'intérieur d'un projet, à partir d'autres projets qui font référence à ce projet et à partir de tout assembly généré à partir de ce projet.  Le code suivant illustre un exemple de déclaration `Public`.  
  
```  
Public Class classForEverybody  
```  
  
 Vous pouvez utiliser le mot clé `Public` seulement au niveau du module, de l'interface ou de l'espace de noms.  En d'autres termes, vous pouvez déclarer un élément public au niveau d'un fichier source ou d'un espace de noms, ou à l'intérieur d'une interface, d'un module, d'une classe ou d'une structure, mais pas dans une procédure.  
  
## Protégé  
 Le mot clé [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) dans l'instruction de déclaration spécifique que les éléments sont accessibles uniquement à partir d'une même classe ou d'une classe dérivée de celle\-ci.  Le code suivant illustre un exemple de déclaration `Protected`.  
  
```  
Protected Class classForMyHeirs  
```  
  
 Vous pouvez utiliser `Protected` uniquement au niveau de la classe et uniquement lors de la déclaration d'un membre d'une classe.  Cela signifie que vous pouvez déclarer un élément protégé dans une classe, mais pas au niveau d'un fichier source ou d'un espace de noms, ni à l'intérieur d'une interface, d'un module, d'une structure ou d'une procédure.  
  
## Friend  
 Le mot clé [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) dans l'instruction de déclaration spécifie que les éléments sont accessibles à partir du même assembly, mais pas à partir de l'extérieur de l'assembly.  Le code suivant illustre un exemple de déclaration `Friend`.  
  
```  
Friend stringForThisProject As String  
```  
  
 Vous pouvez utiliser le mot clé `Friend` seulement au niveau du module, de l'interface ou de l'espace de noms.  En d'autres termes, vous pouvez déclarer un élément "friend" au niveau d'un fichier source ou d'un espace de noms, ou à l'intérieur d'une interface, d'un module, d'une classe ou d'une structure, mais pas dans une procédure.  
  
## Protected Friend  
 Les mots clés `Protected` et `Friend` ensemble dans l'instruction de déclaration spécifient que les éléments sont accessibles soit à partir de classes dérivées, soit à partir du même assembly, soit les deux.  Le code suivant illustre un exemple de déclaration `Protected` `Friend`.  
  
```  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 Vous pouvez utiliser `Protected` `Friend` uniquement au niveau de la classe et uniquement lors de la déclaration d'un membre d'une classe.  Cela signifie que vous pouvez déclarer un élément "protected friend" dans une classe, mais pas au niveau d'un fichier source ou d'un espace de noms, ni à l'intérieur d'une interface, d'un module, d'une structure ou d'une procédure.  
  
## Privé  
 Le mot clé [Private](../../../../visual-basic/language-reference/modifiers/private.md) dans l'instruction de déclaration spécifie que les éléments sont accessibles uniquement à partir du même module, de la même classe ou de la même structure.  Le code suivant illustre un exemple de déclaration `Private`.  
  
```  
Private numberForMeOnly As Integer  
```  
  
 Vous pouvez utiliser `Private` seulement au niveau du module.  Cela signifie que vous pouvez déclarer un élément privé à l'intérieur d'un module, d'une classe ou d'une structure, mais pas au niveau d'un fichier source ou d'un espace de noms, ni à l'intérieur d'une interface ou d'une procédure.  
  
 Au niveau du module, l'instruction `Dim` utilisée sans mot clé de niveau d'accès équivaut à une déclaration `Private`.  Toutefois, il peut s'avérer utile d'utiliser le mot clé `Private` afin que votre code soit plus facile à lire et à interpréter.  
  
## Modificateurs d'accès  
 Les mots clés qui spécifient le niveau d'accès portent le nom de *modificateurs d'accès*.  Le tableau suivant compare les modificateurs d'accès.  
  
|Modificateur d'accès|Niveau d'accès accordé|Éléments que vous pouvez déclarer avec ce niveau d'accès|Contexte de déclaration dans lequel vous pouvez utiliser ce modificateur|  
|--------------------------|----------------------------|--------------------------------------------------------------|------------------------------------------------------------------------------|  
|`Public`|Illimité :<br /><br /> Tout code qui peut voir un élément public peut y accéder|Interfaces<br /><br /> Modules<br /><br /> Classes<br /><br /> Structures<br /><br /> Membres de structures<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> Événements<br /><br /> Déclarations externes<br /><br /> Délégués|Fichier source<br /><br /> Espace de noms<br /><br /> Interface<br /><br /> Module<br /><br /> Classe<br /><br /> Structure|  
|`Protected`|Dérivationnel :<br /><br /> Le code dans la classe qui déclare un élément protégé, ou une classe dérivée d'elle, peut accéder à l'élément|Interfaces<br /><br /> Classes<br /><br /> Structures<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> Événements<br /><br /> Déclarations externes<br /><br /> Délégués|Classe|  
|`Friend`|Assembly :<br /><br /> Le code dans l'assembly qui déclare un élément « friend » peut y accéder|Interfaces<br /><br /> Modules<br /><br /> Classes<br /><br /> Structures<br /><br /> Membres de structures<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> Événements<br /><br /> Déclarations externes<br /><br /> Délégués|Fichier source<br /><br /> Espace de noms<br /><br /> Interface<br /><br /> Module<br /><br /> Classe<br /><br /> Structure|  
|`Protected` `Friend`|Union de `Protected` et `Friend` :<br /><br /> Le code dans la même classe ou le même assembly qu'un élément « protected friend » ou dans toute classe dérivée de la classe de l'élément, peut y accéder|Interfaces<br /><br /> Classes<br /><br /> Structures<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> Événements<br /><br /> Déclarations externes<br /><br /> Délégués|Classe|  
|`Private`|Contexte de déclaration :<br /><br /> Le code dans le type qui déclare un élément privé, y compris code situé dans des types contenus, peut accéder à l'élément|Interfaces<br /><br /> Classes<br /><br /> Structures<br /><br /> Membres de structures<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> Événements<br /><br /> Déclarations externes<br /><br /> Délégués|Module<br /><br /> Classe<br /><br /> Structure|  
  
## Voir aussi  
 [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [How to: Control the Availability of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)   
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)