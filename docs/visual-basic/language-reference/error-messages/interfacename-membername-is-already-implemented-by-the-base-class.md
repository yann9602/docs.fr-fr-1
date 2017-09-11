---
title: "«&lt;interfacename&gt;.&lt; MemberName&gt;&quot;est déjà implémenté par la classe de base&quot;&lt;baseclassname&gt;». Réimplémentation de &lt;type&gt; supposé | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42015
- bc42015
dev_langs:
- VB
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
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
ms.openlocfilehash: d792485f13e2b675858d82aa7219670a17fd974e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a><span data-ttu-id="eeec7-103">«&lt;interfacename&gt;.&lt; MemberName&gt;'est déjà implémenté par la classe de base'&lt;baseclassname&gt;».</span><span class="sxs-lookup"><span data-stu-id="eeec7-103">&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;.</span></span> <span data-ttu-id="eeec7-104">Réimplémentation de &lt;type&gt; supposé</span><span class="sxs-lookup"><span data-stu-id="eeec7-104">Re-implementation of &lt;type&gt; assumed</span></span>
<span data-ttu-id="eeec7-105">Une propriété, une procédure ou un événement dans une classe dérivée utilise un `Implements` clause qui spécifie un membre d’interface qui est déjà implémenté dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="eeec7-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="eeec7-106">Une classe dérivée peut réimplémenter un membre d’interface qui est implémenté par sa classe de base.</span><span class="sxs-lookup"><span data-stu-id="eeec7-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="eeec7-107">La substitution de l’implémentation de la classe de base est une procédure différente.</span><span class="sxs-lookup"><span data-stu-id="eeec7-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="eeec7-108">Pour plus d’informations, consultez [implémente](../../../visual-basic/language-reference/statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="eeec7-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="eeec7-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="eeec7-109">By default, this message is a warning.</span></span> <span data-ttu-id="eeec7-110">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="eeec7-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="eeec7-111">**ID d’erreur :** BC42015</span><span class="sxs-lookup"><span data-stu-id="eeec7-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="eeec7-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="eeec7-112">To correct this error</span></span>  
  
-   <span data-ttu-id="eeec7-113">Si vous comptez réimplémenter le membre d’interface, aucune mesure n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="eeec7-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="eeec7-114">Le code dans votre classe dérivée accède au membre implémenté de nouveau, sauf si vous utilisez la `MyBase` mot clé pour accéder à l’implémentation de classe de base.</span><span class="sxs-lookup"><span data-stu-id="eeec7-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="eeec7-115">Si vous ne comptez pas réimplémenter le membre d’interface, supprimez la clause `Implements` de la déclaration de la propriété, de la procédure ou de l’événement.</span><span class="sxs-lookup"><span data-stu-id="eeec7-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeec7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eeec7-116">See Also</span></span>  
 [<span data-ttu-id="eeec7-117">Interfaces</span><span class="sxs-lookup"><span data-stu-id="eeec7-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
