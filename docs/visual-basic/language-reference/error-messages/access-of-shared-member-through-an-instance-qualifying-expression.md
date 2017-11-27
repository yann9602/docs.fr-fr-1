---
title: "Accès d'un membre partagé via une instance ; l'expression qualifiante ne sera pas évaluée"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42025
- BC42025
helpviewer_keywords: BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bcf3c37852e73464eec612e9e1d458ca707342e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Accès d'un membre partagé via une instance ; l'expression qualifiante ne sera pas évaluée
Une variable d’instance d’une classe ou une structure est utilisée pour accéder à un `Shared` variable, propriété, procédure ou l’événement défini dans cette classe ou structure. Cet avertissement peut également se produire si une variable d’instance est utilisée pour accéder à un membre implicitement partagé d’une classe ou une structure, par exemple une constante ou énumération, ou une classe imbriquée ou une structure.  
  
 Le partage d’un membre vise à créer qu’une seule copie de ce membre et le rendre disponible à chaque instance de la classe ou structure dans laquelle elle est déclarée. Il est conforme à cet effet pour accéder à un `Shared` membre via le nom de sa classe ou structure, plutôt que via une variable qui conserve une instance de cette classe ou structure.  
  
 L’accès à un `Shared` membre via une variable d’instance peut rendre votre code plus difficile à comprendre en masquant le fait que le membre est `Shared`. En outre, si ce type d’accès fait partie d’une expression qui exécute d’autres actions, comme un `Function` procédure qui retourne une instance du membre partagé, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ignore l’expression et autres actions, il doit effectuer dans le cas contraire.  
  
 Pour plus d’informations et obtenir un exemple, consultez [partagé](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [configuration des avertissements en Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42025  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Utilisez le nom de la classe ou structure qui définit le `Shared` membre à y accéder, comme indiqué dans l’exemple suivant.  
  
```vb  
Public Class testClass  
    Public Shared Sub sayHello()  
        MsgBox("Hello")  
    End Sub  
End Class  
  
Module testModule  
    Public Sub Main()  
        ' Access a shared method through an instance variable.  
        ' This generates a warning.  
        Dim tc As New testClass  
        tc.sayHello()  
  
        ' Access a shared method by using the class name.  
        ' This does not generate a warning.  
        testClass.sayHello()  
    End Sub  
End Module  
```  
  
> [!NOTE]
>  Être alerte pour les effets de la portée lorsque deux éléments de programmation portent le même nom. Dans l’exemple précédent, si vous déclarez une instance à l’aide de `Dim testClass as testClass = Nothing`, le compilateur traite un appel à `testClass.sayHello()` comme un accès de la méthode via le nom de classe et aucun avertissement se produit.  
  
## <a name="see-also"></a>Voir aussi  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Portée dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
