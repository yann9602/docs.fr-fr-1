---
title: Usage of Serialization Binder
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e35df7934ffb330feb45e5ff7167c9715f2d291e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="usage-of-serialization-binder"></a><span data-ttu-id="0acc7-102">Usage of Serialization Binder</span><span class="sxs-lookup"><span data-stu-id="0acc7-102">Usage of Serialization Binder</span></span>
<span data-ttu-id="0acc7-103">Cet exemple montre comment utiliser le <xref:System.Runtime.Serialization.SerializationBinder> pour modifier la version d'un type générique lorsqu'il est sérialisé.</span><span class="sxs-lookup"><span data-stu-id="0acc7-103">This sample shows how to use the <xref:System.Runtime.Serialization.SerializationBinder> to change the version of a generic type when it is serialized.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0acc7-104">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="0acc7-104">Demonstrates</span></span>  
 <span data-ttu-id="0acc7-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span><span class="sxs-lookup"><span data-stu-id="0acc7-105"><xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="0acc7-106">Discussion</span><span class="sxs-lookup"><span data-stu-id="0acc7-106">Discussion</span></span>  
 <span data-ttu-id="0acc7-107">Cet exemple montre comment deux entités qui ciblent des versions différentes du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] peuvent communiquer à l'aide du formateur binary et du binder de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="0acc7-107">This sample shows how two entities that are targeting different versions of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] can communicate using the binary formatter and the serialization binder.</span></span>  
  
 <span data-ttu-id="0acc7-108">Le développement de cet exemple a été réalisé à l'aide de .NET Remoting.</span><span class="sxs-lookup"><span data-stu-id="0acc7-108">The development of this sample has been done using .NET Remoting.</span></span> <span data-ttu-id="0acc7-109">L'exemple se compose d'un serveur ciblant [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], qui implémente un contrat avec les types génériques, et deux clients différents, l'un ciblant [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] et l'autre ciblant [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0acc7-109">The sample consists of a server targeting [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], which implements a contract with generic types, and two different clients, one targeting [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] and another targeting [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].</span></span>  
  
 <span data-ttu-id="0acc7-110">Le serveur attache un <xref:System.Runtime.Serialization.SerializationBinder> au formateur binary pour être en mesure de modifier la version des types en conséquence lors de la sérialisation, si les deux clients peuvent désérialiser correctement ces types.</span><span class="sxs-lookup"><span data-stu-id="0acc7-110">The server attaches a <xref:System.Runtime.Serialization.SerializationBinder> to the binary formatter to be able to change the version of the types accordingly on serialization, so both clients can deserialize those types properly.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0acc7-111">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="0acc7-111">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="0acc7-112">Pour exécuter le client, cliquez sur la solution, SBGenericsVTS (6 projets), puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0acc7-112">To execute the client, right-click the solution, SBGenericsVTS (6 projects) and then select **Properties**.</span></span>  
  
2.  <span data-ttu-id="0acc7-113">Dans **propriétés communes**, sélectionnez **projet de démarrage**, puis sélectionnez **plusieurs projets de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="0acc7-113">In **Common Properties**, select **Startup Project**, then select **Multiple Startup Projects**.</span></span>  
  
3.  <span data-ttu-id="0acc7-114">Sélectionnez **Server** premier, puis **Client20** , puis **Client40**.</span><span class="sxs-lookup"><span data-stu-id="0acc7-114">Select **Server** first, then **Client20** and then **Client40**.</span></span> <span data-ttu-id="0acc7-115">Sélectionnez le **Démarrer** action de ces trois projets et laisser le reste de la valeur **aucun**.</span><span class="sxs-lookup"><span data-stu-id="0acc7-115">Select the **Start** action to these three projects and leave the rest set to **None**.</span></span>  
  
4.  <span data-ttu-id="0acc7-116">Cliquez sur **OK** puis appuyez sur F5 pour exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="0acc7-116">Click **OK** and then press F5 to run the sample.</span></span>
