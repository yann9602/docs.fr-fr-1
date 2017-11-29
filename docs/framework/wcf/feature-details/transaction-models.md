---
title: "Modèles de transaction"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 182a394b7698c7a1a59a4db50ee81caed4d2e75f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-models"></a><span data-ttu-id="b6ca9-102">Modèles de transaction</span><span class="sxs-lookup"><span data-stu-id="b6ca9-102">Transaction Models</span></span>
<span data-ttu-id="b6ca9-103">Cette rubrique décrit la relation entre les modèles de programmation de transactions et les composants d’infrastructure que Microsoft fournit.</span><span class="sxs-lookup"><span data-stu-id="b6ca9-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="b6ca9-104">Lors de l'utilisation de transactions dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], il est important de comprendre que vous ne choisissez pas entre des modèles transactionnels différents, mais que vous évoluez dans des couches différentes d'un modèle intégré et cohérent.</span><span class="sxs-lookup"><span data-stu-id="b6ca9-104">When using transactions in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="b6ca9-105">Les sections suivantes décrivent les trois composants principaux d'une transaction.</span><span class="sxs-lookup"><span data-stu-id="b6ca9-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="b6ca9-106">Transactions WCF (Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="b6ca9-106">Windows Communication Foundation Transactions</span></span>  
 <span data-ttu-id="b6ca9-107">La prise en charge des transactions dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vous permet d'écrire des services transactionnels.</span><span class="sxs-lookup"><span data-stu-id="b6ca9-107">The transaction support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows you write transactional services.</span></span> <span data-ttu-id="b6ca9-108">De plus, avec sa prise en charge du protocole WS-AtomicTransaction (WS-AT), les applications peuvent transférer des transactions aux services Web construits à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ou d'une technologie tiers.</span><span class="sxs-lookup"><span data-stu-id="b6ca9-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] or third-party technology.</span></span>  
  
 <span data-ttu-id="b6ca9-109">Dans un service ou une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les fonctionnalités de la transaction [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournissent des attributs et la configuration permettant de spécifier de façon déclarative comment et quand l'infrastructure doit créer, transmettre et synchroniser des transactions.</span><span class="sxs-lookup"><span data-stu-id="b6ca9-109">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="b6ca9-110">Transactions System.Transactions</span><span class="sxs-lookup"><span data-stu-id="b6ca9-110">System.Transactions Transactions</span></span>  
 <span data-ttu-id="b6ca9-111">L'espace de noms <xref:System.Transactions> fournit un modèle de programmation explicite basé sur la classe <xref:System.Transactions.Transaction>, ainsi qu'un modèle de programmation implicite à utilisant la classe <xref:System.Transactions.TransactionScope>, dans lequel l'infrastructure gère automatiquement les transactions.</span><span class="sxs-lookup"><span data-stu-id="b6ca9-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b6ca9-112">comment créer une application transactionnelle à l’aide de ces deux modèles, consultez [l’écriture d’une Application transactionnelle](http://go.microsoft.com/fwlink/?LinkId=94947).</span><span class="sxs-lookup"><span data-stu-id="b6ca9-112"> how to create a transactional application using these two models, see [Writing a Transactional Application](http://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="b6ca9-113">Dans un service ou une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.Transactions> fournit le modèle de programmation pour créer des transactions dans une application cliente et pour interagir explicitement avec une transaction, si nécessaire, au sein d'un service.</span><span class="sxs-lookup"><span data-stu-id="b6ca9-113">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="b6ca9-114">Transactions MSDTC</span><span class="sxs-lookup"><span data-stu-id="b6ca9-114">MSDTC Transactions</span></span>  
 <span data-ttu-id="b6ca9-115">MSDTC (Microsoft Distributed Transaction Coordinator) est un gestionnaire de transactions qui prend en charge les transactions distribuées.</span><span class="sxs-lookup"><span data-stu-id="b6ca9-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="b6ca9-116">le [de référence du programmeur DTC](http://go.microsoft.com/fwlink/?LinkId=94948).</span><span class="sxs-lookup"><span data-stu-id="b6ca9-116"> the [DTC Programmer's Reference](http://go.microsoft.com/fwlink/?LinkId=94948).</span></span>  
  
 <span data-ttu-id="b6ca9-117">Dans un service ou une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], MSDTC fournit l'infrastructure pour la coordination de transactions créées dans un client ou un service.</span><span class="sxs-lookup"><span data-stu-id="b6ca9-117">In a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
