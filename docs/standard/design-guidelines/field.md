---
title: Conception de champs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ccced2c9e816122d770f43056c36ab4a6d510fde
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="field-design"></a><span data-ttu-id="1cf2e-102">Conception de champs</span><span class="sxs-lookup"><span data-stu-id="1cf2e-102">Field Design</span></span>
<span data-ttu-id="1cf2e-103">Le principe d’encapsulation est un des notions plus importantes dans la conception orientée objet.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-103">The principle of encapsulation is one of the most important notions in object-oriented design.</span></span> <span data-ttu-id="1cf2e-104">Ce principe stipule que les données stockées à l’intérieur d’un objet doivent être accessibles uniquement à cet objet.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-104">This principle states that data stored inside an object should be accessible only to that object.</span></span>  
  
 <span data-ttu-id="1cf2e-105">Une méthode utile pour interpréter le principe est à dire qu’un type doit être conçu afin que les modifications aux champs de ce type (modification du nom ou type) peuvent être apportées sans rupture du code autre que pour les membres du type.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-105">A useful way to interpret the principle is to say that a type should be designed so that changes to fields of that type (name or type changes) can be made without breaking code other than for members of the type.</span></span> <span data-ttu-id="1cf2e-106">Cette interprétation implique immédiatement que tous les champs doivent être privées.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-106">This interpretation immediately implies that all fields must be private.</span></span>  
  
 <span data-ttu-id="1cf2e-107">Nous exclure constantes et statiques des champs en lecture seule de cette restriction stricte, car ces champs, presque par définition, ne sont jamais tenus à modifier.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-107">We exclude constant and static read-only fields from this strict restriction, because such fields, almost by definition, are never required to change.</span></span>  
  
 <span data-ttu-id="1cf2e-108">**X ne sont pas** contiennent des champs d’instance qui sont publics ou protégés.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-108">**X DO NOT** provide instance fields that are public or protected.</span></span>  
  
 <span data-ttu-id="1cf2e-109">Vous devez fournir des propriétés pour accéder à des champs au lieu de les rendre publics ou protégés.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-109">You should provide properties for accessing fields instead of making them public or protected.</span></span>  
  
 <span data-ttu-id="1cf2e-110">**✓ FAIRE** utiliser les champs constants pour les constantes qui ne changent pas.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-110">**✓ DO** use constant fields for constants that will never change.</span></span>  
  
 <span data-ttu-id="1cf2e-111">Le compilateur augmente les valeurs des champs const directement dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-111">The compiler burns the values of const fields directly into calling code.</span></span> <span data-ttu-id="1cf2e-112">Par conséquent, les valeurs const ne peuvent jamais être modifiées sans risque de rupture de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-112">Therefore, const values can never be changed without the risk of breaking compatibility.</span></span>  
  
 <span data-ttu-id="1cf2e-113">**✓ FAIRE** utiliser statique public `readonly` champs pour les instances d’objet prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-113">**✓ DO** use public static `readonly` fields for predefined object instances.</span></span>  
  
 <span data-ttu-id="1cf2e-114">S’il existe des instances prédéfinies du type, déclarez les champs statiques en lecture seule comme publics du type lui-même.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-114">If there are predefined instances of the type, declare them as public read-only static fields of the type itself.</span></span>  
  
 <span data-ttu-id="1cf2e-115">**X ne sont pas** affecter des instances de types mutables à `readonly` champs.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-115">**X DO NOT** assign instances of mutable types to `readonly` fields.</span></span>  
  
 <span data-ttu-id="1cf2e-116">Un type mutable est un type avec des instances qui peuvent être modifiées une fois qu’ils sont instanciés.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-116">A mutable type is a type with instances that can be modified after they are instantiated.</span></span> <span data-ttu-id="1cf2e-117">Par exemple, les flux, la plupart des collections et tableaux sont des types mutables, mais <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, et <xref:System.String?displayProperty=nameWithType> sont toutes immuables.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-117">For example, arrays, most collections, and streams are mutable types, but <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>, and <xref:System.String?displayProperty=nameWithType> are all immutable.</span></span> <span data-ttu-id="1cf2e-118">Le modificateur en lecture seule sur un champ de type référence empêche l’instance stockée dans le champ ne soit pas remplacé, mais il n’empêche pas les données d’instance du champ d’être modifié en appelant des membres modification de l’instance.</span><span class="sxs-lookup"><span data-stu-id="1cf2e-118">The read-only modifier on a reference type field prevents the instance stored in the field from being replaced, but it does not prevent the field’s instance data from being modified by calling members changing the instance.</span></span>  
  
 <span data-ttu-id="1cf2e-119">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="1cf2e-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1cf2e-120">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="1cf2e-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf2e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1cf2e-121">See Also</span></span>  
 [<span data-ttu-id="1cf2e-122">Instructions de conception des membres</span><span class="sxs-lookup"><span data-stu-id="1cf2e-122">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="1cf2e-123">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1cf2e-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
