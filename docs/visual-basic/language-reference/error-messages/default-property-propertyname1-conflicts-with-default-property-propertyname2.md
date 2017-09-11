---
title: "Propriété par défaut &quot;&lt;propertyname1&gt;&quot;est en conflit avec la propriété par défaut&quot;&lt;propertyname2&gt;&quot;dans&quot;&lt;classname&gt;&quot; et devrait donc être déclarée &quot;Shadows&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
dev_langs:
- VB
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 9
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
ms.openlocfilehash: 6eac9e0fdc468e27afac82a8a7c9b2251a8f7317
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a><span data-ttu-id="c4477-102">Propriété par défaut '&lt;propertyname1&gt;'est en conflit avec la propriété par défaut'&lt;propertyname2&gt;'dans'&lt;classname&gt;' et devrait donc être déclarée 'Shadows'</span><span class="sxs-lookup"><span data-stu-id="c4477-102">Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;</span></span>
<span data-ttu-id="c4477-103">Une propriété est déclarée avec le même nom qu’une propriété définie dans la classe de base.</span><span class="sxs-lookup"><span data-stu-id="c4477-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="c4477-104">Dans ce cas, la propriété de cette classe doit occulter la propriété de classe de base.</span><span class="sxs-lookup"><span data-stu-id="c4477-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="c4477-105">Ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="c4477-105">This message is a warning.</span></span> <span data-ttu-id="c4477-106">`Shadows`est supposé par défaut.</span><span class="sxs-lookup"><span data-stu-id="c4477-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="c4477-107">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements comme des erreurs, consultez la page [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c4477-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c4477-108">**ID d’erreur :** BC40007</span><span class="sxs-lookup"><span data-stu-id="c4477-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c4477-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="c4477-109">To correct this error</span></span>  
  
-   <span data-ttu-id="c4477-110">Ajouter le `Shadows` mot clé à la déclaration ou changez le nom de la propriété déclarée.</span><span class="sxs-lookup"><span data-stu-id="c4477-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4477-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4477-111">See Also</span></span>  
 <span data-ttu-id="c4477-112">[Ombres](../../../visual-basic/language-reference/modifiers/shadows.md) </span><span class="sxs-lookup"><span data-stu-id="c4477-112">[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) </span></span>  
<span data-ttu-id="c4477-113"> [Occultation dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span><span class="sxs-lookup"><span data-stu-id="c4477-113"> [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)</span></span>
