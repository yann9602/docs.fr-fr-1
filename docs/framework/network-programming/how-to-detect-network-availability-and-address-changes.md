---
title: "Comment : détecter la disponibilité réseau et les changements d’adresse"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Network
ms.assetid: d4377115-4a76-4848-ab23-4898d65c771c
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d6afee9ea1528d4219d32d32fff670ddbfb3033c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-network-availability-and-address-changes"></a><span data-ttu-id="b536f-102">Comment : détecter la disponibilité réseau et les changements d’adresse</span><span class="sxs-lookup"><span data-stu-id="b536f-102">How to: Detect Network Availability and Address Changes</span></span>
<span data-ttu-id="b536f-103">Cet exemple montre comment détecter les modifications de l’adresse réseau d’une interface.</span><span class="sxs-lookup"><span data-stu-id="b536f-103">This sample shows how to detect changes in the network address of an interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b536f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="b536f-104">Example</span></span>  
  
```  
using System;  
using System.Net;  
using System.Net.NetworkInformation;  
  
namespace Examples.Net.AddressChanges  
{  
    public class NetworkingExample  
    {  
        public static void Main()  
        {  
            NetworkChange.NetworkAddressChanged += new   
             NetworkAddressChangedEventHandler(AddressChangedCallback);  
            Console.WriteLine("Listening for address changes. Press any key to exit.");  
            Console.ReadLine();  
        }  
        static void AddressChangedCallback(object sender, EventArgs e)  
        {  
  
            NetworkInterface[] adapters = NetworkInterface.GetAllNetworkInterfaces();  
            foreach(NetworkInterface n in adapters)  
            {  
                Console.WriteLine("   {0} is {1}", n.Name, n.OperationalStatus);  
            }  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b536f-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b536f-105">Compiling the Code</span></span>  
 <span data-ttu-id="b536f-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="b536f-106">This example requires:</span></span>  
  
-   <span data-ttu-id="b536f-107">Références à l’espace de noms **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="b536f-107">References to the **System.Net** namespace.</span></span>
