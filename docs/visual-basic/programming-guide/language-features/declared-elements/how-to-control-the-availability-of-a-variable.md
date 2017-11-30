---
title: "Comment : contrôler la disponibilité d'une variable (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 004fb101661fadeaee084e1f9374ca8332ac7234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>Comment : contrôler la disponibilité d'une variable (Visual Basic)
Contrôle de la disponibilité d’une variable en spécifiant son *niveau d’accès*. Le niveau d’accès détermine quel code est autorisé à lire ou écrire dans la variable.  
  
-   *Variables membres* (défini au niveau du module et en dehors de toute procédure) par défaut d’un accès public, ce qui signifie que tout code qui Affichez-les pour y accéder. Vous pouvez le modifier en spécifiant un modificateur d’accès.  
  
-   *Variables locales* (défini à l’intérieur d’une procédure) nominalement ont un accès public, bien que seul le code dans leur procédure permettre y accéder. Vous ne pouvez pas modifier le niveau d’accès d’une variable locale, mais vous pouvez modifier le niveau d’accès de la procédure qui le contient.  
  
 Pour plus d’informations, consultez [niveaux en Visual Basic d’accès](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Accès privé et Public  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>Pour rendre une variable accessible uniquement à partir de son module, classe ou structure  
  
1.  Place le [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pour la variable à l’intérieur du module, classe ou structure, mais en dehors de toute procédure.  
  
2.  Inclure le [privé](../../../../visual-basic/language-reference/modifiers/private.md) mot clé dans la `Dim` instruction.  
  
     Vous pouvez lire ou écrire dans la variable à partir de n’importe où dans le module, classe ou structure, mais pas à l’extérieur.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>Pour rendre une variable accessible à partir de n’importe quel code qui peut le consulter  
  
1.  Pour une variable membre, placez la `Dim` instruction de la variable à l’intérieur d’un module, classe ou structure, mais en dehors de toute procédure.  
  
2.  Inclure le [Public](../../../../visual-basic/language-reference/modifiers/public.md) mot clé dans la `Dim` instruction.  
  
     Vous pouvez lire ou écrire dans la variable à partir de n’importe quel code qui interagit avec votre assembly.  
  
 ou  
  
1.  Pour une variable locale, placez la `Dim` instruction de la variable à l’intérieur d’une procédure.  
  
2.  N’incluez pas le `Public` mot clé dans la `Dim` instruction.  
  
     Vous pouvez lire ou écrire dans la variable à partir de n’importe où dans la procédure, mais pas à l’extérieur.  
  
## <a name="protected-and-friend-access"></a>Protégé et un accès ami  
 Vous pouvez limiter le niveau d’accès d’une variable à sa classe et toutes les classes dérivées, ou à son assembly. Vous pouvez également spécifier l’union de ces limitations, ce qui autorise l’accès à partir du code dans n’importe quelle classe dérivée ou dans tout autre emplacement dans le même assembly. Vous spécifiez cette union en combinant les `Protected` et `Friend` mots clés dans la même déclaration.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>Pour rendre une variable accessible uniquement à partir de sa classe et toutes les classes dérivées  
  
1.  Place la `Dim` instruction de la variable à l’intérieur d’une classe, mais en dehors de toute procédure.  
  
2.  Inclure le [protégé](../../../../visual-basic/language-reference/modifiers/protected.md) mot clé dans la `Dim` instruction.  
  
     Vous pouvez lire ou écrire dans la variable à partir de n’importe où dans la classe, ainsi que depuis toute classe dérivée à partir de celui-ci, mais pas en dehors de toute classe dans la chaîne de dérivation.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>Pour rendre une variable accessible uniquement à partir du même assembly  
  
1.  Place la `Dim` instruction de la variable à l’intérieur d’un module, classe ou structure, mais en dehors de toute procédure.  
  
2.  Inclure le [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) mot clé dans la `Dim` instruction.  
  
     Vous pouvez lire ou écrire dans la variable à partir de n’importe où dans le module, classe ou structure, ainsi qu’à partir de n’importe quel code dans le même assembly, mais pas à l’extérieur de l’assembly.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre des déclarations de variables avec `Public`, `Protected`, `Friend`, `Protected Friend`, et `Private` niveaux d’accès. Notez que lorsque la `Dim` instruction spécifie un niveau d’accès, vous n’avez pas besoin d’inclure le `Dim` (mot clé).  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Le plus restrictif le niveau d’accès d’une variable, moins vous risquez constituant un code malveillant peut incorrect utiliser.  
  
## <a name="see-also"></a>Voir aussi  
 [Niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Dim (instruction)](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Public](../../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../../visual-basic/language-reference/modifiers/private.md)
