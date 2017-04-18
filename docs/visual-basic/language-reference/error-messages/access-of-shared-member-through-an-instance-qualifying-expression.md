---
title: "Accès de membre partagé via une instance ; l’expression qualifiante ne sera pas évaluée | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42025
- BC42025
dev_langs:
- VB
helpviewer_keywords:
- BC42025
ms.assetid: db3337e5-c349-42bf-86df-d9c1e00952a5
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 39be3c95d5acc20afe3a33be9d4db48c09f99a9c
ms.lasthandoff: 03/13/2017

---
# <a name="access-of-shared-member-through-an-instance-qualifying-expression-will-not-be-evaluated"></a>Accès d'un membre partagé via une instance ; l'expression qualifiante ne sera pas évaluée
Une variable d’instance d’une classe ou une structure est utilisée pour accéder à un `Shared` variable, propriété, procédure ou l’événement défini dans cette classe ou structure. Cet avertissement peut également se produire si une variable d’instance est utilisée pour accéder à un membre implicitement partagé d’une classe ou une structure, comme une constante ou énumération, ou une classe imbriquée ou une structure.  
  
 Le partage d’un membre vise à créer une seule copie de ce membre et le rendre disponible à chaque instance de la classe ou la structure dans laquelle elle est déclarée. Il est cohérent avec ce rôle pour accéder à un `Shared` membre via le nom de sa classe ou structure, plutôt que via une variable qui conserve une instance de cette classe ou structure.  
  
 L’accès à un `Shared` membre via une variable d’instance peut rendre votre code plus difficile à comprendre en masquant le fait que le membre est `Shared`. En outre, si ce type d’accès fait partie d’une expression qui exécute d’autres opérations, comme un `Function` procédure qui retourne une instance du membre partagé, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ignore l’expression et toutes les actions qu’il effectue dans le cas contraire.  
  
 Pour plus d’informations et un exemple, consultez [partagé](../../../visual-basic/language-reference/modifiers/shared.md).  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements comme des erreurs, consultez la page [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42025  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Utilisez le nom de la classe ou structure qui définit les `Shared` membres pour y accéder, comme illustré dans l’exemple suivant.  
  
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
>  Soyez conscient des effets de portée lorsque deux éléments de programmation portent le même nom. Dans l’exemple précédent, si vous déclarez une instance à l’aide de `Dim testClass as testClass = Nothing`, le compilateur traite un appel à `testClass.sayHello()` comme un accès de la méthode via le nom de classe et aucun message d’avertissement se produit.  
  
## <a name="see-also"></a>Voir aussi  
 [Partagé](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Portée dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
