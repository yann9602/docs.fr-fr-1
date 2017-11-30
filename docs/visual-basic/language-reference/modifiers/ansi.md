---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa5724eb9123b2776c3a579e4244c55b3129816b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ansi-visual-basic"></a><span data-ttu-id="478d7-102">Ansi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="478d7-102">Ansi (Visual Basic)</span></span>
<span data-ttu-id="478d7-103">Spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs American National Standards Institute (ANSI), quelle que soit le nom de la procédure externe déclarée.</span><span class="sxs-lookup"><span data-stu-id="478d7-103">Specifies that Visual Basic should marshal all strings to American National Standards Institute (ANSI) values regardless of the name of the external procedure being declared.</span></span>  
  
 <span data-ttu-id="478d7-104">Lorsque vous appelez une procédure définie en dehors de votre projet, le compilateur Visual Basic n’a pas accès aux informations nécessaires appeler la procédure correctement.</span><span class="sxs-lookup"><span data-stu-id="478d7-104">When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it needs to call the procedure correctly.</span></span> <span data-ttu-id="478d7-105">Ces informations comprennent où se trouve la procédure, comment il est identifié, sa séquence d’appel et de type de retour, et chaîne de jeu de caractères qu’il utilise.</span><span class="sxs-lookup"><span data-stu-id="478d7-105">This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses.</span></span> <span data-ttu-id="478d7-106">Le [instruction Declare](../../../visual-basic/language-reference/statements/declare-statement.md) crée une référence à une procédure externe et fournit ces informations nécessaires.</span><span class="sxs-lookup"><span data-stu-id="478d7-106">The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.</span></span>  
  
 <span data-ttu-id="478d7-107">Le `charsetmodifier` dans le cadre de la `Declare` instruction fournit les informations de jeu de caractères pour marshaler des chaînes lors d’un appel à la procédure externe.</span><span class="sxs-lookup"><span data-stu-id="478d7-107">The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure.</span></span> <span data-ttu-id="478d7-108">Elle affecte également la façon dont Visual Basic recherche le fichier externe pour le nom de la procédure externe.</span><span class="sxs-lookup"><span data-stu-id="478d7-108">It also affects how Visual Basic searches the external file for the external procedure name.</span></span> <span data-ttu-id="478d7-109">Le `Ansi` modificateur Spécifie que Visual Basic doit marshaler toutes les chaînes en valeurs ANSI et doit rechercher la procédure sans modifier son nom lors de la recherche.</span><span class="sxs-lookup"><span data-stu-id="478d7-109">The `Ansi` modifier specifies that Visual Basic should marshal all strings to ANSI values and should look up the procedure without modifying its name during the search.</span></span>  
  
 <span data-ttu-id="478d7-110">Si aucun modificateur de jeu de caractères n’est spécifiée, `Ansi` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="478d7-110">If no character set modifier is specified, `Ansi` is the default.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="478d7-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="478d7-111">Remarks</span></span>  
 <span data-ttu-id="478d7-112">Le `Ansi` modificateur peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="478d7-112">The `Ansi` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="478d7-113">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="478d7-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="478d7-114">Remarques sur le développement Smart Device</span><span class="sxs-lookup"><span data-stu-id="478d7-114">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="478d7-115">Ce mot clé n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="478d7-115">This keyword is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="478d7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="478d7-116">See Also</span></span>  
 [<span data-ttu-id="478d7-117">Auto</span><span class="sxs-lookup"><span data-stu-id="478d7-117">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="478d7-118">Unicode</span><span class="sxs-lookup"><span data-stu-id="478d7-118">Unicode</span></span>](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [<span data-ttu-id="478d7-119">Mots clés</span><span class="sxs-lookup"><span data-stu-id="478d7-119">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
