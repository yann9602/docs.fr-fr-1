---
title: "Comment : créer une revendication personnalisée"
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
ms.assetid: d619976b-eda3-475e-ac23-c7988a2dceb0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e1e85d1815d1fbde25e1963a54cce8f02f5344a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-claim"></a><span data-ttu-id="c0d9d-102">Comment : créer une revendication personnalisée</span><span class="sxs-lookup"><span data-stu-id="c0d9d-102">How to: Create a Custom Claim</span></span>
<span data-ttu-id="c0d9d-103">L'infrastructure de modèle d'identité dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournit un ensemble de types et droits de revendication intégrés avec des fonctions d'assistance pour créer des instances <xref:System.IdentityModel.Claims.Claim> avec ces types et droits.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides a set of built-in claim types and rights with the helper functions for creating <xref:System.IdentityModel.Claims.Claim> instances with those types and rights.</span></span> <span data-ttu-id="c0d9d-104">Ces revendications intégrées sont conçues pour modeler données trouvées dans les types d'informations d'identification du client que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] prend en charge par défaut.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-104">These built-in claims are designed to model information found in client credential types that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] supports by default.</span></span> <span data-ttu-id="c0d9d-105">Dans la plupart des cas, les revendications intégrées sont suffisantes ; toutefois, certaines applications peuvent requérir des revendications personnalisées.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-105">In many cases, the built-in claims are sufficient; however some applications may require custom claims.</span></span> <span data-ttu-id="c0d9d-106">Une revendication comporte trois volets : le type de revendication, la ressource à laquelle la revendication s'applique et le droit revendiqué sur cette ressource.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-106">A claim consists of the claim type, the resource for which the claim applies to and the right that is asserted over that resource.</span></span> <span data-ttu-id="c0d9d-107">Cette rubrique décrit comment créer une revendication personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-107">This topic describes how to create a custom claim.</span></span>  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-primitive-data-type"></a><span data-ttu-id="c0d9d-108">Pour créer une revendication personnalisée basée sur un type de données primitif</span><span class="sxs-lookup"><span data-stu-id="c0d9d-108">To create a custom claim that is based on a primitive data type</span></span>  
  
1.  <span data-ttu-id="c0d9d-109">Créez une revendication personnalisée en passant le type de revendication, la valeur de la ressource et le droit sur la ressource au constructeur <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-109">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="c0d9d-110">Choisissez une valeur unique pour le type de revendication.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-110">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="c0d9d-111">Le type de revendication est un identificateur de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-111">The claim type is a unique string identifier.</span></span> <span data-ttu-id="c0d9d-112">Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le type de revendication est unique.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-112">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="c0d9d-113">Pour obtenir une liste des types de revendications définis par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez la classe <xref:System.IdentityModel.Claims.ClaimTypes>.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-113">For a list of claim types that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="c0d9d-114">Choisissez le type de données primitif et la valeur de la ressource.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-114">Choose the primitive data type and value for the resource.</span></span>  
  
         <span data-ttu-id="c0d9d-115">Une ressource est un objet.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-115">A resource is an object.</span></span> <span data-ttu-id="c0d9d-116">Le type CLR de la ressource peut être une primitive, telle que <xref:System.String> ou <xref:System.Int32>, ou tout type sérialisable.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-116">The CLR type of the resource can be a primitive, such as <xref:System.String> or <xref:System.Int32>, or any serializable type.</span></span> <span data-ttu-id="c0d9d-117">Le type CLR de la ressource doit être sérialisable, car les revendications sont sérialisées en différents points par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0d9d-117">The CLR type of the resource must be serializable, because claims are serialized at various points by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="c0d9d-118">Les types primitifs sont sérialisables.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-118">Primitive types are serializable.</span></span>  
  
    3.  <span data-ttu-id="c0d9d-119">Choisissez un droit défini par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ou une valeur unique pour un droit personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-119">Choose a right that is defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="c0d9d-120">Un droit est un identificateur de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-120">A right is a unique string identifier.</span></span> <span data-ttu-id="c0d9d-121">Les droits définis par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] le sont dans la classe <xref:System.IdentityModel.Claims.Rights>.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-121">The rights that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="c0d9d-122">Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le droit est unique.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-122">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="c0d9d-123">L'exemple de code suivant crée une revendication personnalisée avec un type de revendication `http://example.org/claims/simplecustomclaim`, pour une ressource nommée `Driver's License`, et avec le droit <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-123">The following code example creates a custom claim with a claim type of `http://example.org/claims/simplecustomclaim`, for a resource named `Driver's License`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
     [!code-csharp[c_CustomClaim#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#4)]
     [!code-vb[c_CustomClaim#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#4)]  
  
### <a name="to-create-a-custom-claim-that-is-based-on-a-non-primitive-data-type"></a><span data-ttu-id="c0d9d-124">Pour créer une revendication personnalisée basée sur un type de données non primitif</span><span class="sxs-lookup"><span data-stu-id="c0d9d-124">To create a custom claim that is based on a non-primitive data type</span></span>  
  
1.  <span data-ttu-id="c0d9d-125">Créez une revendication personnalisée en passant le type de revendication, la valeur de la ressource et le droit sur la ressource au constructeur <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-125">Create a custom claim by passing the claim type, resource value and right to the <xref:System.IdentityModel.Claims.Claim.%23ctor%28System.String%2CSystem.Object%2CSystem.String%29> constructor.</span></span>  
  
    1.  <span data-ttu-id="c0d9d-126">Choisissez une valeur unique pour le type de revendication.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-126">Decide on a unique value for the claim type.</span></span>  
  
         <span data-ttu-id="c0d9d-127">Le type de revendication est un identificateur de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-127">The claim type is a unique string identifier.</span></span> <span data-ttu-id="c0d9d-128">Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le type de revendication est unique.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-128">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the claim type is unique.</span></span> <span data-ttu-id="c0d9d-129">Pour obtenir une liste des types de revendications définis par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez la classe <xref:System.IdentityModel.Claims.ClaimTypes>.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-129">For a list of claim types that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], see the <xref:System.IdentityModel.Claims.ClaimTypes> class.</span></span>  
  
    2.  <span data-ttu-id="c0d9d-130">Choisissez ou définissez un type non primitif sérialisable pour la ressource.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-130">Choose or define a serializable non-primitive type for the resource.</span></span>  
  
         <span data-ttu-id="c0d9d-131">Une ressource est un objet.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-131">A resource is an object.</span></span> <span data-ttu-id="c0d9d-132">Le type CLR de la ressource doit être sérialisable, car les revendications sont sérialisées en différents points par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0d9d-132">The CLR type of the resource must be serializable, because claims are serialized at various points by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="c0d9d-133">Les types primitifs sont déjà sérialisables.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-133">Primitive types are already serializable.</span></span>  
  
         <span data-ttu-id="c0d9d-134">Lorsqu'un nouveau type est défini, appliquez <xref:System.Runtime.Serialization.DataContractAttribute> à la classe.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-134">When a new type is defined, apply the <xref:System.Runtime.Serialization.DataContractAttribute> to the class.</span></span> <span data-ttu-id="c0d9d-135">Appliquez également l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à tous les membres du nouveau type qui doivent être sérialisés dans le cadre de la revendication.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-135">Also apply the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the all members of the new type that need to be serialized as part of the claim.</span></span>  
  
         <span data-ttu-id="c0d9d-136">L'exemple de code suivant définit un type de ressource personnalisé nommé `MyResourceType`.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-136">The following code example defines a custom resource type named `MyResourceType`.</span></span>  
  
         [!code-csharp[c_CustomClaim#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#2)] 
         [!code-vb[c_CustomClaim#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#2)]        
  
    3.  <span data-ttu-id="c0d9d-137">Choisissez un droit défini par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ou une valeur unique pour un droit personnalisé.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-137">Choose a right that is defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or a unique value for a custom right.</span></span>  
  
         <span data-ttu-id="c0d9d-138">Un droit est un identificateur de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-138">A right is a unique string identifier.</span></span> <span data-ttu-id="c0d9d-139">Les droits définis par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] le sont dans la classe <xref:System.IdentityModel.Claims.Rights>.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-139">The rights that are defined by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are defined in the <xref:System.IdentityModel.Claims.Rights> class.</span></span>  
  
         <span data-ttu-id="c0d9d-140">Il incombe au concepteur de la revendication personnalisée de vérifier que l'identificateur de chaîne utilisé pour le droit est unique.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-140">It is the custom claim designer's responsibility to ensure that the string identifier that is used for the right is unique.</span></span>  
  
         <span data-ttu-id="c0d9d-141">L'exemple de code suivant crée une revendication personnalisée avec un type de revendication `http://example.org/claims/complexcustomclaim`, un type de ressource personnalisé `MyResourceType` et avec le droit <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-141">The following code example creates a custom claim with a claim type of `http://example.org/claims/complexcustomclaim`, a custom resource type of `MyResourceType`, and with the <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> right.</span></span>  
  
         [!code-csharp[c_CustomClaim#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#5)] 
         [!code-vb[c_CustomClaim#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#5)]     
  
## <a name="example"></a><span data-ttu-id="c0d9d-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="c0d9d-142">Example</span></span>  
 <span data-ttu-id="c0d9d-143">L'exemple de code suivant montre comment créer une revendication personnalisée avec un type de ressource primitif et un type de ressource non primitif.</span><span class="sxs-lookup"><span data-stu-id="c0d9d-143">The following code example demonstrates how to create a custom claim with a primitive resource type and a custom claim with a non-primitive resource type.</span></span>  
  
 [!code-csharp[c_CustomClaim#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customclaim/cs/c_customclaim.cs#0)]
 [!code-vb[c_CustomClaim#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customclaim/vb/c_customclaim.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="c0d9d-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0d9d-144">See Also</span></span>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.Rights>  
 <xref:System.IdentityModel.Claims.ClaimTypes>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="c0d9d-145">Gestion des revendications et autorisation avec le modèle d’identité</span><span class="sxs-lookup"><span data-stu-id="c0d9d-145">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="c0d9d-146">Gestion des revendications et autorisation avec le modèle d’identité</span><span class="sxs-lookup"><span data-stu-id="c0d9d-146">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
