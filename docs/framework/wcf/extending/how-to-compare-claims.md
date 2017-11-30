---
title: "Comment : comparer des revendications"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], comparing
- claims [WCF]
ms.assetid: 0c4ec84d-53df-408f-8953-9bc437f56c28
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fd23edd9e390b1f2018419c3c43be8091500c929
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compare-claims"></a><span data-ttu-id="dcabf-102">Comment : comparer des revendications</span><span class="sxs-lookup"><span data-stu-id="dcabf-102">How to: Compare Claims</span></span>
<span data-ttu-id="dcabf-103">L'infrastructure de modèle d'identité dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est utilisée pour effectuer les contrôles d'autorisation.</span><span class="sxs-lookup"><span data-stu-id="dcabf-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] is used to perform authorization checking.</span></span> <span data-ttu-id="dcabf-104">L'une des tâches fréquentes de cette infrastructure de contrôle consiste notamment à comparer les revendications émises dans le cadre des autorisations à celles requises pour l'exécution des requêtes d'action ou des requêtes d'accès aux ressources.</span><span class="sxs-lookup"><span data-stu-id="dcabf-104">As such, a common task is to compare claims in the authorization context to the claims required to perform the requested action or access the requested resource.</span></span> <span data-ttu-id="dcabf-105">Cette rubrique contient des instructions qui permettent de comparer des revendications, notamment les types de revendication intégrés et personnalisés.</span><span class="sxs-lookup"><span data-stu-id="dcabf-105">This topic describes how to compare claims, including built-in and custom claim types.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="dcabf-106">l’infrastructure de modèle d’identité, consultez [la gestion des revendications et autorisation avec le modèle d’identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span><span class="sxs-lookup"><span data-stu-id="dcabf-106"> the Identity Model infrastructure, see [Managing Claims and Authorization with the Identity Model](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).</span></span>  
  
 <span data-ttu-id="dcabf-107">Comparer des revendications signifie comparer leurs trois composantes, à savoir leur type, leurs droits et leurs ressources avec les composantes d'autres revendications, et ce afin de savoir si elles sont égales.</span><span class="sxs-lookup"><span data-stu-id="dcabf-107">Claim comparison involves comparing the three parts of a claim (type, right, and resource) against the same parts in another claim to see if they are equal.</span></span> <span data-ttu-id="dcabf-108">Lisez l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="dcabf-108">See the following example.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#9)]
 [!code-vb[c_CustomClaimComparison#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#9)]  
  
 <span data-ttu-id="dcabf-109">Ces deux revendications partagent le même type de revendication <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, les mêmes droits <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> et une même ressource pour la chaîne "someone".</span><span class="sxs-lookup"><span data-stu-id="dcabf-109">Both claims have a claim type of <xref:System.IdentityModel.Claims.ClaimTypes.Name%2A>, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource of the string "someone".</span></span> <span data-ttu-id="dcabf-110">Leurs trois composantes étant égales, ces deux revendications sont elles-mêmes égales.</span><span class="sxs-lookup"><span data-stu-id="dcabf-110">As all three parts of the claim are equal, the claims themselves are equal.</span></span>  
  
 <span data-ttu-id="dcabf-111">Les types de revendication intégrés sont comparés à l'aide de la méthode <xref:System.IdentityModel.Claims.Claim.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="dcabf-111">The built-in claim types are compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="dcabf-112">Un code de comparaison spécifique à la revendication est utilisé lorsque nécessaire.</span><span class="sxs-lookup"><span data-stu-id="dcabf-112">Claim-specific comparison code is used where necessary.</span></span> <span data-ttu-id="dcabf-113">Prenons, par exemple, les deux revendications suivantes qui utilisent un nom d'utilisateur principal (UPN, User Principal Name) :</span><span class="sxs-lookup"><span data-stu-id="dcabf-113">For example, given the following two user principal name (UPN) claims:</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#4)]
 [!code-vb[c_CustomClaimComparison#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#4)]  
  
 <span data-ttu-id="dcabf-114">le code de comparaison dans la <xref:System.IdentityModel.Claims.Claim.Equals%2A> méthode retourne `true`, en supposant que `example\someone` identifie le même utilisateur de domaine en tant que «someone@example.com».</span><span class="sxs-lookup"><span data-stu-id="dcabf-114">the comparison code in the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method returns `true`, assuming `example\someone` identifies the same domain user as "someone@example.com".</span></span>  
  
 <span data-ttu-id="dcabf-115">Les types de revendication personnalisés peuvent également être comparés à l'aide de la méthode <xref:System.IdentityModel.Claims.Claim.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="dcabf-115">Custom claim types can also be compared using the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="dcabf-116">Toutefois, si le type retourné par la propriété <xref:System.IdentityModel.Claims.Claim.Resource%2A> de la revendication est un type autre que primitif, la méthode <xref:System.IdentityModel.Claims.Claim.Equals%2A> retournera uniquement la valeur `true` si les valeurs retournées par les propriétés `Resource` sont égales selon la méthode <xref:System.IdentityModel.Claims.Claim.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="dcabf-116">However, in cases where the type returned by the <xref:System.IdentityModel.Claims.Claim.Resource%2A> property of the claim is something other than a primitive type, the <xref:System.IdentityModel.Claims.Claim.Equals%2A> returns `true` only if the values returned by the `Resource` properties are equal according to the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span> <span data-ttu-id="dcabf-117">Dans les cas où ce processus ne convient pas, le type personnalisé retourné par la propriété `Resource` doit remplacer les méthodes <xref:System.IdentityModel.Claims.Claim.Equals%2A> et <xref:System.Object.GetHashCode%2A> afin de permettre tous traitements personnalisés requis.</span><span class="sxs-lookup"><span data-stu-id="dcabf-117">In cases where this is not appropriate, the custom type returned by the `Resource` property should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> and <xref:System.Object.GetHashCode%2A> methods to perform whatever custom processing is necessary.</span></span>  
  
### <a name="comparing-built-in-claims"></a><span data-ttu-id="dcabf-118">Comparaison des revendications intégrées</span><span class="sxs-lookup"><span data-stu-id="dcabf-118">Comparing built-in claims</span></span>  
  
1.  <span data-ttu-id="dcabf-119">Soit deux instances de la classe <xref:System.IdentityModel.Claims.Claim>, utilisez la méthode <xref:System.IdentityModel.Claims.Claim.Equals%2A> pour les comparer, tel qu'illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="dcabf-119">Given two instances of the <xref:System.IdentityModel.Claims.Claim> class, use the <xref:System.IdentityModel.Claims.Claim.Equals%2A> to make the comparison, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#5)]
     [!code-vb[c_CustomClaimComparison#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#5)]  
  
### <a name="comparing-custom-claims-with-primitive-resource-types"></a><span data-ttu-id="dcabf-120">Comparaison de revendications personnalisées dont les types de ressources sont primitifs</span><span class="sxs-lookup"><span data-stu-id="dcabf-120">Comparing custom claims with primitive resource types</span></span>  
  
1.  <span data-ttu-id="dcabf-121">Pour les revendications personnalisées dont les types de ressources sont primitifs, la comparaison peut s'effectuer de la même manière que dans le cadre de comparaisons intégrées, tel qu'illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="dcabf-121">For custom claims with primitive resource types, comparison can be performed as for built-in claims, as shown in the following code.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#6)]
     [!code-vb[c_CustomClaimComparison#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#6)]  
  
2.  <span data-ttu-id="dcabf-122">Pour les revendications personnalisées dont les types de ressources sont basés sur une structure ou une classe, le type de ressource doit être substitué à la méthode <xref:System.IdentityModel.Claims.Claim.Equals%2A>.</span><span class="sxs-lookup"><span data-stu-id="dcabf-122">For custom claims with structure or class based resource types, the resource type should override the <xref:System.IdentityModel.Claims.Claim.Equals%2A> method.</span></span>  
  
3.  <span data-ttu-id="dcabf-123">Vérifiez tout d'abord si le paramètre `obj` a la valeur `null`. Si tel est le cas, retournez la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="dcabf-123">First check whether the `obj` parameter is `null`, and if so, return `false`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#7)]
     [!code-vb[c_CustomClaimComparison#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#7)]  
  
4.  <span data-ttu-id="dcabf-124">Appelez ensuite la méthode <xref:System.Object.ReferenceEquals%2A> et passez `this` et `obj` en tant que paramètres.</span><span class="sxs-lookup"><span data-stu-id="dcabf-124">Next call <xref:System.Object.ReferenceEquals%2A> and pass `this` and `obj` as parameters.</span></span> <span data-ttu-id="dcabf-125">Si la méthode appelée retourne la valeur `true`, retournez alors la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="dcabf-125">If it returns `true`, then return `true`.</span></span>  
  
     [!code-csharp[c_CustomClaimComparison#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#8)]
     [!code-vb[c_CustomClaimComparison#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#8)]  
  
5.  <span data-ttu-id="dcabf-126">Essayez ensuite d'affecter `obj` à une variable locale du type de classe.</span><span class="sxs-lookup"><span data-stu-id="dcabf-126">Next attempt to assign `obj` to a local variable of the class type.</span></span> <span data-ttu-id="dcabf-127">En cas d'échec, la référence est `null`.</span><span class="sxs-lookup"><span data-stu-id="dcabf-127">If this fails, the reference is `null`.</span></span> <span data-ttu-id="dcabf-128">Dans ce cas, retournez la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="dcabf-128">In such cases, return `false`.</span></span>  
  
6.  <span data-ttu-id="dcabf-129">Effectuez la comparaison personnalisée nécessaire pour comparer de manière adéquate la revendication en cours à la revendication spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dcabf-129">Perform the custom comparison necessary to correctly compare the current claim to the provided claim.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcabf-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="dcabf-130">Example</span></span>  
 <span data-ttu-id="dcabf-131">L'exemple suivant illustre le cas d'une comparaison où le type de ressource des revendications personnalisées comparées n'est pas primitif.</span><span class="sxs-lookup"><span data-stu-id="dcabf-131">The following example shows a comparison of custom claims where the claim resource is a non-primitive type.</span></span>  
  
 [!code-csharp[c_CustomClaimComparison#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaimcomparison/cs/c_customclaimcomparison.cs#0)]
 [!code-vb[c_CustomClaimComparison#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaimcomparison/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="dcabf-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dcabf-132">See Also</span></span>  
 [<span data-ttu-id="dcabf-133">Gestion des revendications et autorisation avec le modèle d’identité</span><span class="sxs-lookup"><span data-stu-id="dcabf-133">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="dcabf-134">Comment : créer une revendication personnalisée</span><span class="sxs-lookup"><span data-stu-id="dcabf-134">How to: Create a Custom Claim</span></span>](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
