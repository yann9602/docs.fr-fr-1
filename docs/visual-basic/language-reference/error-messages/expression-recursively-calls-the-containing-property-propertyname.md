---
title: "Expression récursivement appelle la propriété conteneur &quot;&lt;propertyname&gt;&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42026
- BC42026
dev_langs:
- VB
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
caps.latest.revision: 10
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
ms.openlocfilehash: ca20bf1a539f2727a80f8e781c1e9ebc5a4a253d
ms.lasthandoff: 03/13/2017

---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a>Expression récursivement appelle la propriété conteneur '&lt;propertyname&gt;»
Une instruction dans le `Set` d’une définition de propriété stocke une valeur dans le nom de la propriété.  
  
 L’approche recommandée pour stocker la valeur d’une propriété consiste à définir un `Private` variable dans le conteneur de la propriété et l’utiliser à la fois dans le `Get` et `Set` procédures. Le `Set` procédure doit ensuite stocker la valeur entrante dans cette `Private` variable.  
  
 Le `Get` procédure se comporte comme un `Function` procédure, afin de pouvoir affecter une valeur au nom de propriété et retourner le contrôle en utilisant la `End Get` instruction. L’approche recommandée, cependant, consiste à inclure le `Private` variable comme valeur dans une [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Le `Set` procédure se comporte comme un `Sub` procédure qui ne retourne pas de valeur. Par conséquent, le nom de la procédure ou la propriété n’a aucune signification spéciale dans un `Set` et vous ne pouvez pas stocker une valeur dedans.  
  
 L’exemple suivant illustre l’approche qui peut provoquer cette erreur, suivie de l’approche recommandée.  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements comme des erreurs, consultez [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42026  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Réécrivez la définition de propriété pour utiliser l’approche recommandée, comme illustré dans l’exemple précédent.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures de propriété](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Set (instruction)](../../../visual-basic/language-reference/statements/set-statement.md)
