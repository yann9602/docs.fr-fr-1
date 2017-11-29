---
title: "Comment : répertorier le contenu d’un répertoire avec FTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 130c64c9-7b7f-4672-9b3b-d946bd2616c5
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f5f74b215fb753d8d5a12a3e203b8598fc258053
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-list-directory-contents-with-ftp"></a><span data-ttu-id="2af55-102">Comment : répertorier le contenu d’un répertoire avec FTP</span><span class="sxs-lookup"><span data-stu-id="2af55-102">How to: List Directory Contents with FTP</span></span>
<span data-ttu-id="2af55-103">Cet exemple montre comment afficher le contenu d’un répertoire d’un serveur FTP.</span><span class="sxs-lookup"><span data-stu-id="2af55-103">This sample shows how to list the directory contents of an FTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2af55-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="2af55-104">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main ()  
        {  
            // Get the object used to communicate with the server.  
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/");  
            request.Method = WebRequestMethods.Ftp.ListDirectoryDetails;  
  
            // This example assumes the FTP site uses anonymous logon.  
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");  
  
            FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
  
            Stream responseStream = response.GetResponseStream();  
            StreamReader reader = new StreamReader(responseStream);  
            Console.WriteLine(reader.ReadToEnd());  
  
            Console.WriteLine("Directory List Complete, status {0}", response.StatusDescription);  
  
            reader.Close();  
            response.Close();  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2af55-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="2af55-105">Compiling the Code</span></span>  
 <span data-ttu-id="2af55-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="2af55-106">This example requires:</span></span>  
  
-   <span data-ttu-id="2af55-107">Références à l’espace de noms **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="2af55-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2af55-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="2af55-108">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2af55-109">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2af55-109">.NET Framework Security</span></span>
