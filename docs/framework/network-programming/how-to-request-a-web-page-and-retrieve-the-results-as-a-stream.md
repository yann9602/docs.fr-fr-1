---
title: "Guide pratique pour demander une page web et récupérer les résultats sous forme de flux"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
caps.latest.revision: 12
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ec19e46289131ec137081c610c1a8194ad22611f
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Guide pratique pour demander une page web et récupérer les résultats sous forme de flux
Cet exemple montre comment demander une page web et récupérer les résultats sous forme de flux.  
  
## <a name="example"></a>Exemple  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Références aux espaces de noms <xref:System.IO> et <xref:System.Net>.  
  
## <a name="see-also"></a>Voir aussi  
 [Demande de données](../../../docs/framework/network-programming/requesting-data.md)

