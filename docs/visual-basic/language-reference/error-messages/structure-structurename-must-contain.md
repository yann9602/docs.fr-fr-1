---
title: "Structure &#39; &lt;nom_structure&gt;&#39; doit contenir variable membre d’au moins une instance ou d’une déclaration d’événement au moins une instance non marquée comme &#39; Custom &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords: BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b28dd59271bdaca52072710ea797fae6e9168eab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a><span data-ttu-id="add4c-102">Structure &#39; &lt;nom_structure&gt;&#39; doit contenir variable membre d’au moins une instance ou d’une déclaration d’événement au moins une instance non marquée comme &#39; Custom &#39;</span><span class="sxs-lookup"><span data-stu-id="add4c-102">Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;</span></span>
<span data-ttu-id="add4c-103">Une définition de structure n’inclut pas toutes les variables non partagées ou des événements non personnalisés non partagées.</span><span class="sxs-lookup"><span data-stu-id="add4c-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="add4c-104">Chaque structure doit avoir une variable ou un événement qui s’applique à chaque instance spécifique (non partagée) et non à toutes les instances collectivement ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="add4c-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="add4c-105">Les procédures, les propriétés et les constantes non partagées ne répondent pas à cette exigence.</span><span class="sxs-lookup"><span data-stu-id="add4c-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="add4c-106">En outre, s’il y a aucune variable non partagée et qu’un seul événement non partagé, cet événement ne peut pas être un `Custom` événement.</span><span class="sxs-lookup"><span data-stu-id="add4c-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="add4c-107">**ID d’erreur :** BC30941</span><span class="sxs-lookup"><span data-stu-id="add4c-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="add4c-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="add4c-108">To correct this error</span></span>  
  
-   <span data-ttu-id="add4c-109">Définissez au moins une variable ou un événement qui n’est pas `Shared`.</span><span class="sxs-lookup"><span data-stu-id="add4c-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="add4c-110">Si vous définissez un seul événement, il doit être non personnalisés ainsi que non partagée.</span><span class="sxs-lookup"><span data-stu-id="add4c-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="add4c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="add4c-111">See Also</span></span>  
 [<span data-ttu-id="add4c-112">Structures</span><span class="sxs-lookup"><span data-stu-id="add4c-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="add4c-113">Guide pratique : déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="add4c-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="add4c-114">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="add4c-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
