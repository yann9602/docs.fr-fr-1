---
title: Instructions de conception pour les exceptions
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], exceptions
- errors [.NET Framework], exceptions
- reporting errors
ms.assetid: bc177b2f-7528-4ae4-83db-aacfb04b86d0
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ee456632070f778d51d7fb40475a795a0f620b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="design-guidelines-for-exceptions"></a><span data-ttu-id="afea4-102">Instructions de conception pour les exceptions</span><span class="sxs-lookup"><span data-stu-id="afea4-102">Design Guidelines for Exceptions</span></span>
<span data-ttu-id="afea4-103">La gestion des exceptions présente de nombreux avantages sur le rapport d’erreurs de basée sur la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="afea4-103">Exception handling has many advantages over return-value-based error reporting.</span></span> <span data-ttu-id="afea4-104">Conception bon framework permet le développeur d’applications de tirer parti d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="afea4-104">Good framework design helps the application developer realize the benefits of exceptions.</span></span> <span data-ttu-id="afea4-105">Cette section présente les avantages des exceptions et présente des indications pour les utiliser efficacement.</span><span class="sxs-lookup"><span data-stu-id="afea4-105">This section discusses the benefits of exceptions and presents guidelines for using them effectively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="afea4-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="afea4-106">In This Section</span></span>  
 [<span data-ttu-id="afea4-107">Levée d’exceptions</span><span class="sxs-lookup"><span data-stu-id="afea4-107">Exception Throwing</span></span>](../../../docs/standard/design-guidelines/exception-throwing.md)  
 [<span data-ttu-id="afea4-108">À l’aide des Types d’Exception Standard</span><span class="sxs-lookup"><span data-stu-id="afea4-108">Using Standard Exception Types</span></span>](../../../docs/standard/design-guidelines/using-standard-exception-types.md)  
 [<span data-ttu-id="afea4-109">Exceptions et performances</span><span class="sxs-lookup"><span data-stu-id="afea4-109">Exceptions and Performance</span></span>](../../../docs/standard/design-guidelines/exceptions-and-performance.md)  
 <span data-ttu-id="afea4-110">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="afea4-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="afea4-111">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="afea4-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afea4-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afea4-112">See Also</span></span>  
 [<span data-ttu-id="afea4-113">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="afea4-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
