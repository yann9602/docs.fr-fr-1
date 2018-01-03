---
title: "Comment : accéder aux propriétés spécifiques à HTTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 3800883307ad0d25677b7feeae15d865c8d2d9d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-http-specific-properties"></a><span data-ttu-id="75107-102">Comment : accéder aux propriétés spécifiques à HTTP</span><span class="sxs-lookup"><span data-stu-id="75107-102">How to: Access HTTP-Specific Properties</span></span>
<span data-ttu-id="75107-103">Cet exemple montre comment désactiver le comportement HTTP **Keep-alive** et obtenir le numéro de version du protocole du serveur web.</span><span class="sxs-lookup"><span data-stu-id="75107-103">This sample shows how to turn off the HTTP **Keep-alive** behavior and get the protocol version number from the Web server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75107-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="75107-104">Example</span></span>  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =   
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="75107-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="75107-105">Compiling the Code</span></span>  
 <span data-ttu-id="75107-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="75107-106">This example requires:</span></span>  
  
-   <span data-ttu-id="75107-107">Références à l’espace de noms **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="75107-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75107-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75107-108">See Also</span></span>  
 [<span data-ttu-id="75107-109">Accès à Internet via un proxy</span><span class="sxs-lookup"><span data-stu-id="75107-109">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="75107-110">Utilisation de protocoles d’application</span><span class="sxs-lookup"><span data-stu-id="75107-110">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="75107-111">HTTP</span><span class="sxs-lookup"><span data-stu-id="75107-111">HTTP</span></span>](../../../docs/framework/network-programming/http.md)
