---
title: "«&lt;elementname&gt;&quot; est obsolète (avertissement Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40008
- bc40008
dev_langs:
- VB
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 12
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
ms.openlocfilehash: 77708f052f7aec7a5da2b24605ba3bd794f83979
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="39ltelementnamegt39-is-obsolete-visual-basic-warning"></a><span data-ttu-id="d35b4-102">«&lt;elementname&gt;' est obsolète (avertissement Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d35b4-102">&#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="d35b4-103">Une instruction essaie d’accéder à un élément de programmation qui a été marqué avec la <xref:System.ObsoleteAttribute>attribut et la directive pour le traiter comme un avertissement.</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="d35b4-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="d35b4-104">Vous pouvez marquer les éléments de programmation comme n’étant plus utilisé par l’application <xref:System.ObsoleteAttribute>à celui-ci.</xref:System.ObsoleteAttribute></span><span class="sxs-lookup"><span data-stu-id="d35b4-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="d35b4-105">Si vous procédez ainsi, vous pouvez définir l’attribut <xref:System.ObsoleteAttribute.IsError%2A>propriété `True` ou `False`.</xref:System.ObsoleteAttribute.IsError%2A></span><span class="sxs-lookup"><span data-stu-id="d35b4-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="d35b4-106">Si vous lui affectez la valeur `True`, le compilateur traite une tentative d’utilisation de l’élément comme une erreur.</span><span class="sxs-lookup"><span data-stu-id="d35b4-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="d35b4-107">Si vous lui affectez la valeur `False`, ou si vous laissez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d’utilisation de l’élément.</span><span class="sxs-lookup"><span data-stu-id="d35b4-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="d35b4-108">Par défaut, ce message est un avertissement, car la <xref:System.ObsoleteAttribute.IsError%2A>propriété du <xref:System.ObsoleteAttribute>est `False`.</xref:System.ObsoleteAttribute> </xref:System.ObsoleteAttribute.IsError%2A></span><span class="sxs-lookup"><span data-stu-id="d35b4-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="d35b4-109">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements comme des erreurs, consultez la page [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d35b4-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d35b4-110">**ID d’erreur :** BC40008</span><span class="sxs-lookup"><span data-stu-id="d35b4-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d35b4-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="d35b4-111">To correct this error</span></span>  
  
-   <span data-ttu-id="d35b4-112">Vérifiez que le nom de l’élément est orthographié correctement dans la référence du code source.</span><span class="sxs-lookup"><span data-stu-id="d35b4-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d35b4-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d35b4-113">See Also</span></span>  
 [<span data-ttu-id="d35b4-114">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="d35b4-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

