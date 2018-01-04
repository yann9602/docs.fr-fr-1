---
title: Comparaison des transactions dans COM+ et dans ServiceModel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87e3df31060a9c71e0b2868aa34373bca221fa79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a><span data-ttu-id="14306-102">Comparaison des transactions dans COM+ et dans ServiceModel</span><span class="sxs-lookup"><span data-stu-id="14306-102">Comparing Transactions in COM+ and ServiceModel</span></span>
<span data-ttu-id="14306-103">Cette rubrique explique comment simuler le comportement d'un service COM+ transactionnel à l'aide des attributs [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] fournis par l'espace de noms <xref:System.ServiceModel>.</span><span class="sxs-lookup"><span data-stu-id="14306-103">This topic discusses how to simulate the behavior of a transactional COM+ service using the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
## <a name="emulating-com-using-servicemodel-attributes"></a><span data-ttu-id="14306-104">Émulation de COM+ à l'aide d'attributs ServiceModel</span><span class="sxs-lookup"><span data-stu-id="14306-104">Emulating COM+ Using ServiceModel Attributes</span></span>  
 <span data-ttu-id="14306-105">Le tableau suivant compare l'énumération <xref:System.EnterpriseServices.TransactionOption> utilisée pour créer une transaction `EnterpriseServices` et la manière dont elles sont corrélées aux attributs [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournis par l'espace de noms <xref:System.ServiceModel>.</span><span class="sxs-lookup"><span data-stu-id="14306-105">The following table compares the <xref:System.EnterpriseServices.TransactionOption> enumeration used to create an `EnterpriseServices` transaction and how they correlate to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attributes the <xref:System.ServiceModel> namespace provides.</span></span>  
  
|<span data-ttu-id="14306-106">Attribut COM+</span><span class="sxs-lookup"><span data-stu-id="14306-106">COM+ attribute</span></span>|<span data-ttu-id="14306-107">Attributs [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14306-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] attributes</span></span>|  
|---------------------|------------------------------------------------------------------------|  
|<span data-ttu-id="14306-108">RequiresNew</span><span class="sxs-lookup"><span data-stu-id="14306-108">RequiresNew</span></span>|<span data-ttu-id="14306-109"><xref:System.ServiceModel.TransactionFlowAttribute> a la valeur <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span><span class="sxs-lookup"><span data-stu-id="14306-109"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span></span><br /><br /> <span data-ttu-id="14306-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="14306-110"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="14306-111">L'attribut `TransactionFlow` dans l'élément de liaison a la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="14306-111">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="14306-112">Obligatoire</span><span class="sxs-lookup"><span data-stu-id="14306-112">Required</span></span>|<span data-ttu-id="14306-113"><xref:System.ServiceModel.TransactionFlowAttribute> a la valeur <xref:System.ServiceModel.TransactionFlowOption.Allowed>.</span><span class="sxs-lookup"><span data-stu-id="14306-113"><xref:System.ServiceModel.TransactionFlowAttribute> is set to <xref:System.ServiceModel.TransactionFlowOption.Allowed>.</span></span><br /><br /> <span data-ttu-id="14306-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="14306-114"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `true`.</span></span><br /><br /> <span data-ttu-id="14306-115">L'attribut `TransactionFlow` dans l'élément de liaison a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="14306-115">The `TransactionFlow` attribute in the binding element is `true`.</span></span>|  
|<span data-ttu-id="14306-116">Pris en charge</span><span class="sxs-lookup"><span data-stu-id="14306-116">Supported</span></span>|<span data-ttu-id="14306-117">Il n'existe pas d'équivalent direct.</span><span class="sxs-lookup"><span data-stu-id="14306-117">There is no direct equivalent.</span></span> <span data-ttu-id="14306-118">En général, vous devez à la place adopter le comportement spécifié pour `Required`.</span><span class="sxs-lookup"><span data-stu-id="14306-118">In general, you should adopt the behavior specified for `Required` instead.</span></span>|  
|<span data-ttu-id="14306-119">Non pris en charge</span><span class="sxs-lookup"><span data-stu-id="14306-119">NotSupported</span></span>|<span data-ttu-id="14306-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="14306-120"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> is `false`.</span></span><br /><br /> <span data-ttu-id="14306-121">L'attribut `TransactionFlow` dans l'élément de liaison a la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="14306-121">The `TransactionFlow` attribute in the binding element is `false`.</span></span>|  
|<span data-ttu-id="14306-122">Disabled</span><span class="sxs-lookup"><span data-stu-id="14306-122">Disabled</span></span>|<span data-ttu-id="14306-123">Il n'existe pas d'équivalent direct.</span><span class="sxs-lookup"><span data-stu-id="14306-123">There is no direct equivalent.</span></span> <span data-ttu-id="14306-124">En général, vous devez à la place adopter le comportement spécifié pour `NotSupported`.</span><span class="sxs-lookup"><span data-stu-id="14306-124">In general, you should adopt the behavior specified for `NotSupported` instead.</span></span>|
