---
title: "API et bibliothèques de classes supplémentaires"
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c22de3ed401e0be10b155649395da43cedb35e6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="additional-class-libraries-and-apis"></a>API et bibliothèques de classes supplémentaires

Le .NET Framework est en constante évolution et pour améliorer le développement multiplateforme ou proposer des nouveautés à nos clients à un stade précoce, nous diffusons les nouvelles fonctionnalités hors bande (OOB). Cette rubrique répertorie les projets OOB pour lesquels nous fournissons une documentation.  
  
En outre, certaines bibliothèques ciblent des plateformes ou des implémentations précises du .NET Framework. Par exemple, la <xref:System.Text.CodePagesEncodingProvider> classe rend les codages de pages de code disponibles pour les applications UWP développées à l’aide de .NET Framework. Cette rubrique liste également ces bibliothèques.  
  
## <a name="oob-projects"></a>Projets OOB
  
| Projet | Description |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | Fournit des collections thread-safe dont le contenu est assuré de ne jamais changer. |
| <xref:System.Net.Http.WinHttpHandler> | Fournit un gestionnaire de messages pour <xref:System.Net.Http.HttpClient> basé sur l’interface WinHTTP de Windows. |
| [System.Numerics.Vectors](https://msdn.microsoft.com/library/mt452176.aspx) | Fournit une bibliothèque de types de vecteurs qui peuvent tirer parti de l’accélération matérielle SIMD.| 
| <xref:System.Threading.Tasks.Dataflow> | La bibliothèque de flux de données TPL fournit des composants de flux de données destinés à accroître la robustesse des applications prenant en charge l’accès concurrentiel. |  

## <a name="platform-specific-libraries"></a>Bibliothèques propres à une plateforme
  
| Projet | Description |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Étend la <xref:System.Text.EncodingProvider> classe pour rendre les codages de pages de code disponibles pour les applications qui ciblent la plateforme Windows universelle. |  
  
## <a name="private-apis"></a>API privées  

Ces API prennent en charge l'infrastructure du produit et ne sont ni utilisables ni destinées à être utilisées directement à partir du code.  
  
| Nom de l'API |
| -------- |
| [Classe de System.Net.Connection](../../../docs/framework/additional-apis/connection.md) |
| [System.Net.Connection.m\_WriteList champ](../../../docs/framework/additional-apis/m_writelist.md) |
| [Classe de System.Net.ConnectionGroup](../../../docs/framework/additional-apis/connectiongroup.md) |
| [System.Net.ConnectionGroup.m\_ConnectionList champ](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [System.Net.HttpWebRequest. \_HttpResponse champ](../../../docs/framework/additional-apis/_httpresponse.md) |
| [System.Net.HttpWebRequest. \_AutoRedirects champ](../../../docs/framework/additional-apis/_autoredirects.md) |
| [System.Net.ServicePoint.m\_ConnectionGroupList champ](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [System.Net.ServicePointManager.s\_ServicePointTable champ](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes champ](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [Classe de System.Windows.Forms.Design.DataMemberFieldEditor](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [Classe de System.Windows.Forms.Design.DataMemberListEditor](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>Voir aussi

[Versions finales hors plage de .NET Framework](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
