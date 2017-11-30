---
title: "Niveaux d'accès dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 87e43ac7e813cece1179bdaf24c86fa62adcb438
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="access-levels-in-visual-basic"></a>Niveaux d'accès dans Visual Basic
Le *niveau d’accès* d’un élément déclaré est l’étendue de la possibilité d’y accéder, autrement dit, le code qui a autorisé à le lire ou écrire dessus. Ceci est déterminé par la façon dont vous déclarez l’élément lui-même, mais également le niveau d’accès du conteneur de l’élément. Code qui ne peut pas accéder à un élément conteneur ne peut pas accéder à un de ses éléments contenus, même ceux déclarés `Public`. Par exemple, un `Public` variable dans un `Private` structure sont accessibles à partir de la classe qui contient la structure, mais pas en dehors de cette classe.  
  
## <a name="public"></a>Public  
 Le [Public](../../../../visual-basic/language-reference/modifiers/public.md) mot clé dans l’instruction de déclaration spécifie que les éléments sont accessibles à partir du code n’importe où dans le même projet, à partir d’autres projets faisant référence au projet et à partir de tout assembly généré à partir du projet. Le code suivant montre un exemple `Public` déclaration.  
  
```  
Public Class classForEverybody  
```  
  
 Vous pouvez utiliser `Public` uniquement au niveau du module, interface ou espace de noms. Cela signifie que vous pouvez déclarer un élément public au niveau d’un fichier source ou un espace de noms, ou à l’intérieur d’une interface, un module, une classe ou une structure, mais pas dans une procédure.  
  
## <a name="protected"></a>Protected  
 Le [protégé](../../../../visual-basic/language-reference/modifiers/protected.md) mot clé dans l’instruction de déclaration spécifie que les éléments sont accessibles uniquement à partir d’une dans la même classe ou d’une classe dérivée de cette classe. Le code suivant montre un exemple `Protected` déclaration.  
  
```  
Protected Class classForMyHeirs  
```  
  
 Vous pouvez utiliser `Protected` uniquement au niveau de la classe de niveau et uniquement lorsque vous déclarez un membre d’une classe. Cela signifie que vous pouvez déclarer un élément protégé dans une classe, mais pas au niveau d’un fichier source ou un espace de noms, ou à l’intérieur d’une interface, un module, une structure ou une procédure.  
  
## <a name="friend"></a>Friend  
 Le [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) mot clé dans l’instruction de déclaration spécifie que les éléments accessibles à partir du même assembly, mais pas à l’extérieur de l’assembly. Le code suivant montre un exemple `Friend` déclaration.  
  
```  
Friend stringForThisProject As String  
```  
  
 Vous pouvez utiliser `Friend` uniquement au niveau du module, interface ou espace de noms. Cela signifie que vous pouvez déclarer un élément friend au niveau d’un fichier source ou un espace de noms, ou à l’intérieur d’une interface, un module, une classe ou une structure, mais pas dans une procédure.  
  
## <a name="protected-friend"></a>Protected Friend  
 Le `Protected` et `Friend` mots clés ensemble dans l’instruction de déclaration spécifient que les éléments est accessible à partir de classes dérivées ou à partir du même assembly, ou les deux. Le code suivant montre un exemple `Protected Friend` déclaration.  
  
```  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 Vous pouvez utiliser `Protected Friend` uniquement au niveau de la classe de niveau et uniquement lorsque vous déclarez un membre d’une classe. Cela signifie que vous pouvez déclarer un élément friend protégé dans une classe, mais pas au niveau d’un fichier source ou un espace de noms, ou à l’intérieur d’une interface, un module, une structure ou une procédure.  
  
## <a name="private"></a>Private  
 Le [privé](../../../../visual-basic/language-reference/modifiers/private.md) mot clé dans l’instruction de déclaration spécifie que les éléments sont accessibles uniquement à partir de dans le même module, classe ou structure. Le code suivant montre un exemple `Private` déclaration.  
  
```  
Private numberForMeOnly As Integer  
```  
  
 Vous pouvez utiliser `Private` seulement au niveau du module. Cela signifie que vous pouvez déclarer un élément privé à l’intérieur d’un module, classe ou structure, mais pas au niveau d’un fichier source ou un espace de noms, à l’intérieur d’une interface, ou dans une procédure.  
  
 Au niveau du module, le `Dim` instruction sans le mot clé de niveau d’accès est équivalente à une `Private` déclaration. Toutefois, vous souhaiterez peut-être utiliser le `Private` mot clé pour rendre votre code plus facile à lire et interpréter.  
  
## <a name="access-modifiers"></a>Modificateurs d’accès  
 Les mots clés qui spécifient le niveau d’accès sont appelés *les modificateurs d’accès*. Le tableau suivant compare les modificateurs d’accès.  
  
|Modificateur d’accès|Niveau d’accès accordé|Vous pouvez déclarer avec ce niveau d’accès des éléments|Contexte de déclaration dans lequel vous pouvez utiliser ce modificateur|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|Unrestricted :<br /><br /> Tout code qui peut voir un élément public peut y accéder|Interfaces<br /><br /> Modules<br /><br /> Classes<br /><br /> Structures<br /><br /> Membres de structure<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> Événements<br /><br /> Déclarations externes<br /><br /> Délégués|Fichier source<br /><br /> Espace de noms<br /><br /> Interface<br /><br /> Module<br /><br /> Classe<br /><br /> Structure|  
|`Protected`|Qui :<br /><br /> Dans la classe qui déclare un élément protégé, ou une classe dérivée à partir de celui-ci, peut accéder à l’élément de code|Interfaces<br /><br /> Classes<br /><br /> Structures<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> Événements<br /><br /> Déclarations externes<br /><br /> Délégués|Classe|  
|`Friend`|Assembly :<br /><br /> Le code dans l’assembly qui déclare qu'un élément friend permettre y accéder|Interfaces<br /><br /> Modules<br /><br /> Classes<br /><br /> Structures<br /><br /> Membres de structure<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> Événements<br /><br /> Déclarations externes<br /><br /> Délégués|Fichier source<br /><br /> Espace de noms<br /><br /> Interface<br /><br /> Module<br /><br /> Classe<br /><br /> Structure|  
|`Protected` `Friend`|Union de `Protected` et `Friend`:<br /><br /> Dans la même classe ou le même assembly en tant qu’un élément friend protégé, ou dans toute classe dérivée de la classe de l’élément de code, peuvent y accéder|Interfaces<br /><br /> Classes<br /><br /> Structures<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> Événements<br /><br /> Déclarations externes<br /><br /> Délégués|Classe|  
|`Private`|Contexte de déclaration :<br /><br /> Code dans le type qui déclare un élément privé, y compris le code au sein de types de contenus, peut accéder à l’élément|Interfaces<br /><br /> Classes<br /><br /> Structures<br /><br /> Membres de structure<br /><br /> Procédures<br /><br /> Propriétés<br /><br /> Variables membres<br /><br /> Constantes<br /><br /> Énumérations<br /><br /> Événements<br /><br /> Déclarations externes<br /><br /> Délégués|Module<br /><br /> Classe<br /><br /> Structure|  
  
## <a name="see-also"></a>Voir aussi  
 [Dim (instruction)](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)  
 [Noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Caractéristiques d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Durée de vie dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Portée dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Guide pratique : contrôler la disponibilité d’une variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
