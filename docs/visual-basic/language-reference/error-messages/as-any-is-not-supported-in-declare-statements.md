---
title: '&quot;As Any&quot; n&quot;est pas pris en charge dans les instructions &quot;Declare&quot; | Documents Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30828
- vbc30828
dev_langs:
- VB
helpviewer_keywords:
- BC30828
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: 11
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
ms.openlocfilehash: bed9beb0c34c1a918029cc7fac4f8c97950eee23
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="39as-any39-is-not-supported-in-39declare39-statements"></a><span data-ttu-id="b02a9-102">'As Any' n'est pas pris en charge dans les instructions 'Declare'</span><span class="sxs-lookup"><span data-stu-id="b02a9-102">&#39;As Any&#39; is not supported in &#39;Declare&#39; statements</span></span>
<span data-ttu-id="b02a9-103">Le `Any` type de données a été utilisé avec `Declare` instructions dans Visual Basic 6.0 et les versions antérieures pour permettre d’utiliser des arguments pouvant contenir tout type de données.</span><span class="sxs-lookup"><span data-stu-id="b02a9-103">The `Any` data type was used with `Declare` statements in Visual Basic 6.0 and earlier versions to permit the use of arguments that could contain any type of data.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="b02a9-104">prend en charge la surcharge, toutefois et rend ainsi le `Any` du type de données obsolète.</span><span class="sxs-lookup"><span data-stu-id="b02a9-104"> supports overloading, however, and so makes the `Any` data type obsolete.</span></span>  
  
 <span data-ttu-id="b02a9-105">**ID d’erreur :** BC30828</span><span class="sxs-lookup"><span data-stu-id="b02a9-105">**Error ID:** BC30828</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b02a9-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="b02a9-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="b02a9-107">Déclarer des paramètres du type spécifique que vous souhaitez utiliser. par exemple.</span><span class="sxs-lookup"><span data-stu-id="b02a9-107">Declare parameters of the specific type you want to use; for example.</span></span>  
  
     <span data-ttu-id="b02a9-108">[!code-vb[VbVbalrStatements&#95;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b02a9-108">[!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_1.vb)]</span></span>  
  
2.  <span data-ttu-id="b02a9-109">Utilisez le <xref:System.Runtime.InteropServices.MarshalAsAttribute>attribut pour spécifier `As Any` lorsque `Void*` est attendu par la procédure appelée.</xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="b02a9-109">Use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to specify `As Any` when `Void*` is expected by the procedure being called.</span></span>  
  
     <span data-ttu-id="b02a9-110">[!code-vb[VbVbalrStatements&#96;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b02a9-110">[!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/as-any-is-not-supported-in-declare-statements_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b02a9-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b02a9-111">See Also</span></span>  
 <span data-ttu-id="b02a9-112"><xref:System.Runtime.InteropServices.MarshalAsAttribute></xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="b02a9-112"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span></span>   
<span data-ttu-id="b02a9-113"> [Procédure pas à pas : Appel des API Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md) </span><span class="sxs-lookup"><span data-stu-id="b02a9-113"> [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md) </span></span>  
<span data-ttu-id="b02a9-114"> [Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b02a9-114"> [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) </span></span>  
<span data-ttu-id="b02a9-115"> [Création de Prototypes dans du Code managé](http://msdn.microsoft.com/library/ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d)</span><span class="sxs-lookup"><span data-stu-id="b02a9-115"> [Creating Prototypes in Managed Code](http://msdn.microsoft.com/library/ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d)</span></span>
