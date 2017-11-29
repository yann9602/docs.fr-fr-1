---
title: "&#39; En tant que &#39; n’est pas pris en charge dans &#39; Declare &#39; instructions"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
helpviewer_keywords: BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59120622688ee38d5b8f45c08dfc3ae40711fb8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a><span data-ttu-id="bf0a1-102">&#39; En tant que &#39; n’est pas pris en charge dans &#39; Declare &#39; instructions</span><span class="sxs-lookup"><span data-stu-id="bf0a1-102">&#39;As Any&#39; is not supported in &#39;Declare&#39; statements</span></span>
<span data-ttu-id="bf0a1-103">Le `Any` type de données a été utilisé avec `Declare` instructions dans Visual Basic 6.0 et versions antérieures pour permettre l’utilisation d’arguments qui peut contenir n’importe quel type de données.</span><span class="sxs-lookup"><span data-stu-id="bf0a1-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="bf0a1-104">prend en charge la surcharge, toutefois et rend ainsi le `Any` de type de données obsolète.</span><span class="sxs-lookup"><span data-stu-id="bf0a1-104"> supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="bf0a1-105">**ID d’erreur :** BC30828</span><span class="sxs-lookup"><span data-stu-id="bf0a1-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bf0a1-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="bf0a1-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="bf0a1-107">Déclarer des paramètres du type spécifique que vous souhaitez utiliser. par exemple.</span><span class="sxs-lookup"><span data-stu-id="bf0a1-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]  
  
2.  <span data-ttu-id="bf0a1-108">Utilisez le <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribut pour spécifier `As Any` lorsque `Void*` est attendue par la procédure appelée.</span><span class="sxs-lookup"><span data-stu-id="bf0a1-108">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bf0a1-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf0a1-109">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="bf0a1-110">Procédure pas à pas : appel des API Windows</span><span class="sxs-lookup"><span data-stu-id="bf0a1-110">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="bf0a1-111">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="bf0a1-111">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="bf0a1-112">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="bf0a1-112">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)
