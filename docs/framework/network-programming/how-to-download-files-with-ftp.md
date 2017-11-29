---
title: "Comment : télécharger des fichiers avec FTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 892548b8-954a-4f6a-9bca-2ae620c3700f
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 656a8de6a508d6834fd1866df14ec5378d4f84af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-download-files-with-ftp"></a><span data-ttu-id="d21a2-102">Comment : télécharger des fichiers avec FTP</span><span class="sxs-lookup"><span data-stu-id="d21a2-102">How to: Download Files with FTP</span></span>
<span data-ttu-id="d21a2-103">Cet exemple montre comment télécharger un fichier à partir d’un serveur FTP.</span><span class="sxs-lookup"><span data-stu-id="d21a2-103">This sample shows how to download a file from an FTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d21a2-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="d21a2-104">Example</span></span>  
  
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
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/test.htm");  
            request.Method = WebRequestMethods.Ftp.DownloadFile;  
  
            // This example assumes the FTP site uses anonymous logon.  
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");  
  
            FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
  
            Stream responseStream = response.GetResponseStream();  
            StreamReader reader = new StreamReader(responseStream);  
            Console.WriteLine(reader.ReadToEnd());  
  
            Console.WriteLine("Download Complete, status {0}", response.StatusDescription);  
  
            reader.Close();  
            response.Close();    
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d21a2-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="d21a2-105">Compiling the Code</span></span>  
 <span data-ttu-id="d21a2-106">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="d21a2-106">This example requires:</span></span>  
  
-   <span data-ttu-id="d21a2-107">Références à l’espace de noms **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="d21a2-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d21a2-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="d21a2-108">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d21a2-109">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d21a2-109">.NET Framework Security</span></span>
