---
title: "&#39; Get &#39; accesseur de propriété &#39; &lt;propertyname&gt;&#39; n’est pas accessible"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords: BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 167e040570af1fc78ce48f5e930e54981ba909ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="39get39-accessor-of-property-39ltpropertynamegt39-is-not-accessible"></a><span data-ttu-id="11da0-102">&#39; Get &#39; accesseur de propriété &#39; &lt;propertyname&gt;&#39; n’est pas accessible</span><span class="sxs-lookup"><span data-stu-id="11da0-102">&#39;Get&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible</span></span>
<span data-ttu-id="11da0-103">Une instruction essaie de récupérer la valeur d’une propriété qui n’a pas accès à la propriété `Get` procédure.</span><span class="sxs-lookup"><span data-stu-id="11da0-103">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>  
  
 <span data-ttu-id="11da0-104">Si le [instruction Get](../../../visual-basic/language-reference/statements/get-statement.md) est marquée avec un accès plus restrictif niveau que son [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md), une tentative de lecture de la valeur de propriété peut échouer dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="11da0-104">If the [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>  
  
-   <span data-ttu-id="11da0-105">Le `Get` instruction est marquée [privé](../../../visual-basic/language-reference/modifiers/private.md) et le code appelant est en dehors de la classe ou structure dans laquelle la propriété est définie.</span><span class="sxs-lookup"><span data-stu-id="11da0-105">The `Get` statement is marked [Private](../../../visual-basic/language-reference/modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>  
  
-   <span data-ttu-id="11da0-106">Le `Get` instruction est marquée [protégé](../../../visual-basic/language-reference/modifiers/protected.md) et le code appelant n’est pas dans la classe ou structure dans laquelle la propriété est définie, ni dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="11da0-106">The `Get` statement is marked [Protected](../../../visual-basic/language-reference/modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>  
  
-   <span data-ttu-id="11da0-107">Le `Get` instruction est marquée [Friend](../../../visual-basic/language-reference/modifiers/friend.md) et le code appelant n’est pas dans le même assembly dans lequel la propriété est définie.</span><span class="sxs-lookup"><span data-stu-id="11da0-107">The `Get` statement is marked [Friend](../../../visual-basic/language-reference/modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>  
  
 <span data-ttu-id="11da0-108">**ID d’erreur :** BC31103</span><span class="sxs-lookup"><span data-stu-id="11da0-108">**Error ID:** BC31103</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="11da0-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="11da0-109">To correct this error</span></span>  
  
-   <span data-ttu-id="11da0-110">Si vous avez le contrôle de code source qui définit la propriété, vous devez déclarer le `Get` procédure avec le même niveau d’accès en tant que la propriété proprement dite.</span><span class="sxs-lookup"><span data-stu-id="11da0-110">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>  
  
-   <span data-ttu-id="11da0-111">Si vous n’avez pas de contrôle de code source qui définit la propriété, ou vous devez limiter la `Get` procédure niveau d’accès plus de la propriété proprement dite, essayez de déplacer l’instruction qui lit la valeur de propriété à une région de code qui offre un meilleur accès à la propriété.</span><span class="sxs-lookup"><span data-stu-id="11da0-111">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11da0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="11da0-112">See Also</span></span>  
 [<span data-ttu-id="11da0-113">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="11da0-113">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="11da0-114">Guide pratique : déclarer une propriété avec des niveaux d’accès mixtes</span><span class="sxs-lookup"><span data-stu-id="11da0-114">How to: Declare a Property with Mixed Access Levels</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
