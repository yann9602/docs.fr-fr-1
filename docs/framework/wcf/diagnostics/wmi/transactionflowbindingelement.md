---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b073efc47ccc1708bf4c58153b1001a21eee25f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="55b2a-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="55b2a-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="55b2a-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="55b2a-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55b2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55b2a-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="55b2a-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="55b2a-105">Methods</span></span>  
 <span data-ttu-id="55b2a-106">La classe TransactionFlowBindingElement ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="55b2a-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="55b2a-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="55b2a-107">Properties</span></span>  
 <span data-ttu-id="55b2a-108">La classe TransactionFlowBindingElement dispose des propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="55b2a-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="55b2a-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="55b2a-109">IssuedTokens</span></span>  
 <span data-ttu-id="55b2a-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="55b2a-110">Data type: string</span></span>  
  
 <span data-ttu-id="55b2a-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="55b2a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="55b2a-112">Définit les exigences d’un en-tête de jetons de sécurité publié (IssuedTokens de WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="55b2a-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="55b2a-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="55b2a-113">TransactionProtocol</span></span>  
 <span data-ttu-id="55b2a-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="55b2a-114">Data type: string</span></span>  
  
 <span data-ttu-id="55b2a-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="55b2a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="55b2a-116">Protocole de transactions utilisé par le service pour transférer les transactions.</span><span class="sxs-lookup"><span data-stu-id="55b2a-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="55b2a-117">Transactions</span><span class="sxs-lookup"><span data-stu-id="55b2a-117">Transactions</span></span>  
 <span data-ttu-id="55b2a-118">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="55b2a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="55b2a-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="55b2a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="55b2a-120">Indique si la transaction entrante est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="55b2a-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55b2a-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="55b2a-121">Requirements</span></span>  
  
|<span data-ttu-id="55b2a-122">MOF</span><span class="sxs-lookup"><span data-stu-id="55b2a-122">MOF</span></span>|<span data-ttu-id="55b2a-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="55b2a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="55b2a-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="55b2a-124">Namespace</span></span>|<span data-ttu-id="55b2a-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="55b2a-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55b2a-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55b2a-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
