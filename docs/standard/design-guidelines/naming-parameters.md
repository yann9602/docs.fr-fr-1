---
title: "Attribution d'un nom à des paramètres"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a10fa8835bfbcf826f8a3bb9318966e0dc603864
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="naming-parameters"></a><span data-ttu-id="95a37-102">Attribution d'un nom à des paramètres</span><span class="sxs-lookup"><span data-stu-id="95a37-102">Naming Parameters</span></span>
<span data-ttu-id="95a37-103">Au-delà de la raison évidente de lisibilité, il est important de suivre les instructions pour les noms de paramètre, car les paramètres sont affichés dans la documentation et dans le concepteur lorsque les outils de conception visuelle fournissent Intellisense et la classe de fonctionnalités de navigation.</span><span class="sxs-lookup"><span data-stu-id="95a37-103">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>  
  
 <span data-ttu-id="95a37-104">**✓ FAIRE** utilisez la casse mixte dans les noms de paramètre.</span><span class="sxs-lookup"><span data-stu-id="95a37-104">**✓ DO** use camelCasing in parameter names.</span></span>  
  
 <span data-ttu-id="95a37-105">**✓ FAIRE** utiliser des noms de paramètres descriptifs.</span><span class="sxs-lookup"><span data-stu-id="95a37-105">**✓ DO** use descriptive parameter names.</span></span>  
  
 <span data-ttu-id="95a37-106">**✓ Envisagez** à l’aide de noms basés sur la signification du paramètre plutôt que le type de paramètre.</span><span class="sxs-lookup"><span data-stu-id="95a37-106">**✓ CONSIDER** using names based on a parameter’s meaning rather than the parameter’s type.</span></span>  
  
### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="95a37-107">Paramètres de surcharge d’opérateur d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="95a37-107">Naming Operator Overload Parameters</span></span>  
 <span data-ttu-id="95a37-108">**✓ FAIRE** utiliser `left` et `right` opérateur binaire surchargé aux noms de paramètres s’il n’a aucune signification pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="95a37-108">**✓ DO** use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="95a37-109">**✓ FAIRE** utiliser `value` pour unaire surcharge d’opérateur les noms de paramètres s’il n’a aucune signification pour les paramètres.</span><span class="sxs-lookup"><span data-stu-id="95a37-109">**✓ DO** use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>  
  
 <span data-ttu-id="95a37-110">**✓ Envisagez** des noms explicites pour l’opérateur de paramètres de surcharge si cela ajoute une valeur significative.</span><span class="sxs-lookup"><span data-stu-id="95a37-110">**✓ CONSIDER** meaningful names for operator overload parameters if doing so adds significant value.</span></span>  
  
 <span data-ttu-id="95a37-111">**X ne sont pas** les noms de paramètres de surcharge des abréviations d’utilisation ou un index numérique pour l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="95a37-111">**X DO NOT** use abbreviations or numeric indices for operator overload parameter names.</span></span>  
  
 <span data-ttu-id="95a37-112">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="95a37-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="95a37-113">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="95a37-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a37-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95a37-114">See Also</span></span>  
 [<span data-ttu-id="95a37-115">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="95a37-115">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="95a37-116">Directives de nommage</span><span class="sxs-lookup"><span data-stu-id="95a37-116">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
