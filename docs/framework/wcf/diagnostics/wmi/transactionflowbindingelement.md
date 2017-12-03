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
ms.openlocfilehash: fa5394e874e35b80b01796642e18d69c71e867dc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="transactionflowbindingelement"></a><span data-ttu-id="98e74-102">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="98e74-102">TransactionFlowBindingElement</span></span>
<span data-ttu-id="98e74-103">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="98e74-103">TransactionFlowBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e74-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98e74-104">Syntax</span></span>  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="98e74-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="98e74-105">Methods</span></span>  
 <span data-ttu-id="98e74-106">La classe TransactionFlowBindingElement ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="98e74-106">The TransactionFlowBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="98e74-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="98e74-107">Properties</span></span>  
 <span data-ttu-id="98e74-108">La classe TransactionFlowBindingElement dispose des propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="98e74-108">The TransactionFlowBindingElement class has the following properties:</span></span>  
  
### <a name="issuedtokens"></a><span data-ttu-id="98e74-109">IssuedTokens</span><span class="sxs-lookup"><span data-stu-id="98e74-109">IssuedTokens</span></span>  
 <span data-ttu-id="98e74-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="98e74-110">Data type: string</span></span>  
  
 <span data-ttu-id="98e74-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="98e74-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98e74-112">Définit les spécifications d'un en-tête de jetons de sécurité publié (IssuedTokens de WS-Trust).</span><span class="sxs-lookup"><span data-stu-id="98e74-112">Specifies the requirement for an issued security tokens header (IssuedTokens from WS-Trust).</span></span>  
  
### <a name="transactionprotocol"></a><span data-ttu-id="98e74-113">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="98e74-113">TransactionProtocol</span></span>  
 <span data-ttu-id="98e74-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="98e74-114">Data type: string</span></span>  
  
 <span data-ttu-id="98e74-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="98e74-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98e74-116">Protocole de transactions utilisé par le service pour transférer les transactions.</span><span class="sxs-lookup"><span data-stu-id="98e74-116">The transactions protocol used by the service to flow transactions.</span></span>  
  
### <a name="transactions"></a><span data-ttu-id="98e74-117">Transactions</span><span class="sxs-lookup"><span data-stu-id="98e74-117">Transactions</span></span>  
 <span data-ttu-id="98e74-118">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="98e74-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="98e74-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="98e74-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98e74-120">Indique si la transaction entrante est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="98e74-120">Indicates whether the incoming transaction is supported.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98e74-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="98e74-121">Requirements</span></span>  
  
|<span data-ttu-id="98e74-122">MOF</span><span class="sxs-lookup"><span data-stu-id="98e74-122">MOF</span></span>|<span data-ttu-id="98e74-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="98e74-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="98e74-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="98e74-124">Namespace</span></span>|<span data-ttu-id="98e74-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="98e74-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98e74-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98e74-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
