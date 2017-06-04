---
title: "Comment&#160;: utiliser Svcutil.exe pour t&#233;l&#233;charger des documents de m&#233;tadonn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Comment&#160;: utiliser Svcutil.exe pour t&#233;l&#233;charger des documents de m&#233;tadonn&#233;es
Svcutil.exe vous permet de télécharger des métadonnées à partir de systèmes en cours d'exécution et de les enregistrer dans des fichiers locaux.Pour les schémas d'URL HTTP et HTTPS, Svcutil.exe tente de récupérer les métadonnées à l'aide de WS\-MetadataExchange et du processus [Découverte d'un service Web XML](http://go.microsoft.com/fwlink/?LinkId=94950) \(page pouvant être en anglais\).Pour tous les autres schémas d'URL, Svcutil.exe utilise uniquement WS\-MetadataExchange.  
  
 Par défaut, Svcutil.exe utilise les liaisons définies dans la classe <xref:System.ServiceModel.Description.MetadataExchangeBindings>.Pour configurer la liaison utilisée pour WS\-MetadataExchange, vous devez définir un point de terminaison client dans le fichier de configuration de Svcutil.exe \(svcutil.exe.config\) qui utilise le contrat `IMetadataExchange` et qui porte le même nom que le schéma d'URI \(Uniform Resource Identifier\) de l'adresse du point de terminaison des métadonnées.  
  
> [!CAUTION]
>  Lors de l'exécution de Svcutil.exe pour obtenir des métadonnées pour un service qui expose deux contrats de service différents contenant chacun une opération du même nom, Svcutil.exe affiche une erreur indiquant « Impossible d'obtenir les métadonnées à partir de .... ». Par exemple, vous avez un service qui expose un contrat de service appelé ICarService avec une opération Get\(Voiture c\) et le même service expose un contrat de service appelé IBookService avec une opération Get\(Livre b\).Pour remédier à ce problème, effectuez l'une des opérations suivantes :  
>   
>  -   Renommez l'une des opérations  
> -   Affectez au <xref:System.ServiceModel.OperationContractAttribute.Name%2A> un nom différent.  
> -   Affectez à l'un des espaces de noms des opérations un espace de noms différent à l'aide de la propriété <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.  
  
### Pour télécharger les métadonnées à l'aide de Svcutil.exe  
  
1.  Localisez l'outil Svcutil.exe à l'emplacement suivant :  
  
     C:\\Program Files\\Microsoft SDKs\\Windows\\v1.0.\\bin  
  
2.  À l'invite de commandes, lancez l'outil en utilisant le format suivant.  
  
    ```  
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     Vous devez spécifier l'option `/t:metadata` pour télécharger les métadonnées.Sinon, la configuration et le code client seront générés.  
  
3.  L'argument \<`url`\> spécifie l'URL à un point de terminaison de service qui fournit les métadonnées ou à un document de métadonnées hébergé en ligne.L'argument \<`epr`\> spécifie le chemin d'accès à un fichier XML contenant un `EndpointAddress` WS\-Addressing pour un point de terminaison de service qui prend en charge WS\-MetadataExchange.  
  
 Pour obtenir davantage d'options sur l'utilisation de cet outil dans le cadre du téléchargement de métadonnées, consultez [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## Exemple  
 La commande suivante télécharge des documents de métadonnées à partir d'un service en cours d'exécution.  
  
```  
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## Voir aussi  
 [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)