---
title: "Comment : créer et utiliser une fabrication de canal pour créer et gérer des canaux"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 018dcc30-9f61-419e-af8e-412a85e8d282
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cb2e8384fca96149babb5df01e25a1b890db6ad3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels"></a><span data-ttu-id="4bd4d-102">Comment : créer et utiliser une fabrication de canal pour créer et gérer des canaux</span><span class="sxs-lookup"><span data-stu-id="4bd4d-102">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>
<span data-ttu-id="4bd4d-103">La classe <xref:System.ServiceModel.DuplexChannelFactory%601> offre des outils qui permettent de créer et de gérer des canaux duplex de différents types utilisés ensuite par les clients pour envoyer des messages vers des points de terminaison de service ou en recevoir à partir de ces mêmes points.</span><span class="sxs-lookup"><span data-stu-id="4bd4d-103">The <xref:System.ServiceModel.DuplexChannelFactory%601> class provides the means to create and manage duplex channels of different types that clients use to send and receive messages to and from service endpoints.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bd4d-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="4bd4d-104">Example</span></span>  
 <span data-ttu-id="4bd4d-105">L'exemple de code suivant indique comment créer une fabrication de canal et l'utiliser ensuite pour créer et gérer des canaux.</span><span class="sxs-lookup"><span data-stu-id="4bd4d-105">The following code shows how to create a channel factory and use it to create and manage channels.</span></span>  
  
 [!code-csharp[S_CustomAuthentication#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_customauthentication/cs/instance.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4bd4d-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bd4d-106">See Also</span></span>  
 <xref:System.ServiceModel.DuplexChannelFactory%601>
