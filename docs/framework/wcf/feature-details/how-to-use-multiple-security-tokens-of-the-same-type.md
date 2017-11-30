---
title: "Comment : utiliser plusieurs jetons de sécurité du même type"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9827d43ba4b0693d16380d93b066948d464bb978
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="e2b3c-102">Comment : utiliser plusieurs jetons de sécurité du même type</span><span class="sxs-lookup"><span data-stu-id="e2b3c-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
-   <span data-ttu-id="e2b3c-103">Dans le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, un message client ne pouvait contenir qu'un jeton d'un type donné.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-103">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="e2b3c-104">Désormais, les messages peuvent contenir plusieurs jetons d'un type donné.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="e2b3c-105">Cette rubrique explique comment inclure plusieurs jetons du même type dans un message client.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
-   <span data-ttu-id="e2b3c-106">Notez que vous ne pouvez pas configurer un service ainsi : un service peut contenir un seul jeton de prise en charge.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="e2b3c-107">Pour utiliser plusieurs jetons de sécurité du même type</span><span class="sxs-lookup"><span data-stu-id="e2b3c-107">To use multiple security tokens of the same type</span></span>  
  
1.  <span data-ttu-id="e2b3c-108">Créez une collection d'éléments de liaison vide à remplir.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  <span data-ttu-id="e2b3c-109">Créez un <xref:System.ServiceModel.Channels.SecurityBindingElement> en appelant <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  <span data-ttu-id="e2b3c-110">Créez une collection <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  <span data-ttu-id="e2b3c-111">Ajoutez des jetons SAML à la collection.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  <span data-ttu-id="e2b3c-112">Ajoutez la collection à <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  <span data-ttu-id="e2b3c-113">Ajoutez des éléments de liaison à la collection d'éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  <span data-ttu-id="e2b3c-114">Retournez une nouvelle liaison personnalisée créée à partir de la collection d’éléments de liaison.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="e2b3c-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="e2b3c-115">Example</span></span>  
 <span data-ttu-id="e2b3c-116">Vous trouverez ci-dessous la méthode complète décrite par la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="e2b3c-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2b3c-117">See Also</span></span>  
 [<span data-ttu-id="e2b3c-118">Architecture de sécurité</span><span class="sxs-lookup"><span data-stu-id="e2b3c-118">Security Architecture</span></span>](http://msdn.microsoft.com/en-us/16593476-d36a-408d-808c-ae6fd483e28f)
