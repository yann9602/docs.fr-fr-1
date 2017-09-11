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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c7168ab2a2ec5eb0c0d423120b67c10b117c14b2
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a><span data-ttu-id="97f40-102">Expression récursivement appelle la propriété conteneur '&lt;propertyname&gt;»</span><span class="sxs-lookup"><span data-stu-id="97f40-102">Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39;</span></span>
<span data-ttu-id="97f40-103">Une instruction dans le `Set` d’une définition de propriété stocke une valeur dans le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="97f40-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="97f40-104">L’approche recommandée pour stocker la valeur d’une propriété consiste à définir un `Private` variable dans le conteneur de la propriété et l’utiliser à la fois dans le `Get` et `Set` procédures.</span><span class="sxs-lookup"><span data-stu-id="97f40-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="97f40-105">Le `Set` procédure doit ensuite stocker la valeur entrante dans cette `Private` variable.</span><span class="sxs-lookup"><span data-stu-id="97f40-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="97f40-106">Le `Get` procédure se comporte comme un `Function` procédure, afin de pouvoir affecter une valeur au nom de propriété et retourner le contrôle en utilisant la `End Get` instruction.</span><span class="sxs-lookup"><span data-stu-id="97f40-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="97f40-107">L’approche recommandée, cependant, consiste à inclure le `Private` variable comme valeur dans une [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="97f40-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="97f40-108">Le `Set` procédure se comporte comme un `Sub` procédure qui ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="97f40-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="97f40-109">Par conséquent, le nom de la procédure ou la propriété n’a aucune signification spéciale dans un `Set` et vous ne pouvez pas stocker une valeur dedans.</span><span class="sxs-lookup"><span data-stu-id="97f40-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="97f40-110">L’exemple suivant illustre l’approche qui peut provoquer cette erreur, suivie de l’approche recommandée.</span><span class="sxs-lookup"><span data-stu-id="97f40-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
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
  
 <span data-ttu-id="97f40-111">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="97f40-111">By default, this message is a warning.</span></span> <span data-ttu-id="97f40-112">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements comme des erreurs, consultez [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="97f40-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="97f40-113">**ID d’erreur :** BC42026</span><span class="sxs-lookup"><span data-stu-id="97f40-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="97f40-114">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="97f40-114">To correct this error</span></span>  
  
-   <span data-ttu-id="97f40-115">Réécrivez la définition de propriété pour utiliser l’approche recommandée, comme illustré dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="97f40-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f40-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="97f40-116">See Also</span></span>  
 <span data-ttu-id="97f40-117">[Procédures de propriété](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="97f40-117">[Property Procedures](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md) </span></span>  
<span data-ttu-id="97f40-118"> [Property (instruction)](../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="97f40-118"> [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="97f40-119"> [Set (instruction)](../../../visual-basic/language-reference/statements/set-statement.md)</span><span class="sxs-lookup"><span data-stu-id="97f40-119"> [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)</span></span>
