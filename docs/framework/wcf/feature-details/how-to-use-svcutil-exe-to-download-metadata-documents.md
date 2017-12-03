---
title: "Comment : utiliser Svcutil.exe pour télécharger des documents de métadonnées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6868bbecd83305c07e0b547d0102d7bca48d41f8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a>Comment : utiliser Svcutil.exe pour télécharger des documents de métadonnées
Svcutil.exe vous permet de télécharger des métadonnées à partir de systèmes en cours d'exécution et de les enregistrer dans des fichiers locaux. Pour les schémas d’URL HTTP et HTTPS, Svcutil.exe essaie de récupérer les métadonnées à l’aide de WS-MetadataExchange et [détection du Service Web XML](http://go.microsoft.com/fwlink/?LinkId=94950). Pour tous les autres schémas d'URL, Svcutil.exe utilise uniquement WS-MetadataExchange.  
  
 Par défaut, Svcutil.exe utilise les liaisons définies dans la classe <xref:System.ServiceModel.Description.MetadataExchangeBindings>. Pour configurer la liaison utilisée pour WS-MetadataExchange, vous devez définir un point de terminaison client dans le fichier de configuration de Svcutil.exe (svcutil.exe.config) qui utilise le contrat `IMetadataExchange` et qui porte le même nom que le schéma d'URI (Uniform Resource Identifier) de l'adresse du point de terminaison des métadonnées.  
  
> [!CAUTION]
>  Lorsque Svcutil.exe pour obtenir des métadonnées pour un service qui expose deux autre service en cours d’exécution de contrats que chacune contenir une opération du même nom, Svcutil.exe affiche une erreur disant « Impossible d’obtenir les métadonnées à partir de... » Par exemple, si vous avez un service qui expose un contrat de service appelé ICarService comportant une opération Get (voiture c) et le même service expose un contrat de service appelé IBookService comportant une opération Get (livre b). Pour remédier à ce problème, effectuez l'une des opérations suivantes :  
>   
>  -   Renommez l'une des opérations  
> -   Affectez au <xref:System.ServiceModel.OperationContractAttribute.Name%2A> un nom différent.  
> -   Affectez à l'un des espaces de noms des opérations un espace de noms différent à l'aide de la propriété <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.  
  
### <a name="to-download-metadata-using-svcutilexe"></a>Pour télécharger les métadonnées à l'aide de Svcutil.exe  
  
1.  Localisez l'outil Svcutil.exe à l'emplacement suivant :  
  
     C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin  
  
2.  À l'invite de commandes, lancez l'outil en utilisant le format suivant.  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Vous devez spécifier l'option `/t:metadata` pour télécharger les métadonnées. Sinon, la configuration et le code client seront générés.  
  
3.  Le <`url`> argument spécifie l’URL à un point de terminaison de service qui fournit des métadonnées ou à un document de métadonnées hébergé en ligne. Le <`epr`> argument spécifie le chemin d’accès à un fichier XML qui contient un WS-Addressing `EndpointAddress` pour un point de terminaison de service qui prend en charge WS-MetadataExchange.  
  
 Pour plus d’options sur l’utilisation de cet outil de téléchargement de métadonnées, consultez [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="example"></a>Exemple  
 La commande suivante télécharge des documents de métadonnées à partir d'un service en cours d'exécution.  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Outil ServiceModel Metadata Utility (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
