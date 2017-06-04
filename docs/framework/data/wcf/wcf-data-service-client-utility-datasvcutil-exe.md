---
title: "Utilitaire client WCF Data Services (DataSvcUtil.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Services de données WCF, bibliothèque cliente"
  - "Services de données WCF, consommation"
  - "Services de données WCF, génération de classes de données clientes"
ms.assetid: 9d0af606-929b-4c03-b307-3ef5f705afce
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Utilitaire client WCF Data Services (DataSvcUtil.exe)
DataSvcUtil.exe est un outil en ligne de commande fourni par [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] qui consomme un flux [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] et génère les classes de service de données client nécessaires pour accéder à un service de données depuis une application cliente .NET Framework.  Cet utilitaire peut générer des classes de données à l'aide des sources de métadonnées suivantes :  
  
-   URI racine d'un service de données.  L'utilitaire demande le document des métadonnées du service, qui décrit le modèle de données exposé par le service de données.  Pour plus d'informations, consultez [OData : document des métadonnées d'un service](http://go.microsoft.com/fwlink/?LinkId=186070).  
  
-   Fichier modèle de données \(.csdl\) défini à l'aide du langage CSDL \(Conceptual Schema Definition Language\), selon les termes de la spécification [\[MC\-CSDL\] : format du fichier de définition d'un schéma conceptuel](http://go.microsoft.com/fwlink/?LinkID=159072).  
  
-   Fichier .edmx créé à l'aide des outils Entity Data Model fournis avec l'Entity Framework.  Pour plus d'informations, consultez la spécification [\[MC\-EDMX\] : modèle de données des entités pour le format du packaging des services de données](http://go.microsoft.com/fwlink/?LinkID=178833).  
  
 Pour plus d'informations, consultez [Procédure : générer manuellement des classes de service de données client](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
 L'outil DataSvcUtil.exe est installé dans le répertoire [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  Dans de nombreux cas, celui\-ci se trouve dans C:\\Windows\\Microsoft.NET\\Framework\\v4.0.  Pour les systèmes 64 bits, il se trouve dans C:\\Windows\\Microsoft.NET\\Framework64\\v4.0.  Vous pouvez également accéder à l'outil DataSvcUtil.exe à partir de l'invite de commandes de Microsoft Visual Studio \(cliquez sur **Démarrer**, pointez sur **Tous les programmes**, sur **Microsoft Visual Studio 2010** et sur **Outils Visual Studio**, puis cliquez sur **Invite de commandes de Visual Studio 2010**\).  
  
## Syntaxe  
  
```  
datasvcutil /out:file [/in:file | /uri:serviceuri] [/dataservicecollection] [/language:devlang] [/nologo] [/version:ver] [/help]  
```  
  
#### Paramètres  
  
|Option|Description|  
|------------|-----------------|  
|`/dataservicecollection`|Spécifie que le code nécessaire pour lier des objets aux contrôles est également généré.|  
|`/help`<br /><br /> ou<br /><br /> `/?`|Affiche la syntaxe et les options de commande de l'outil.|  
|`/in:` *\<fichier\>*|Spécifie le fichier .csdl ou .edmx ou un répertoire qui contient le fichier.|  
|`/language:`\[VB&#124;CSharp\]|Spécifie le langage des fichiers de code source générés.  Le langage par défaut est C\#.|  
|`/nologo`|Supprime l'affichage du message de copyright.|  
|`/out:` *\<fichier\>*|Spécifie le nom du fichier de code source qui contient les classes de service de données client générées.|  
|`/uri:` *\<string\>*|URI du flux [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].|  
|`/version:`\[1.0&#124;2.0\]|Spécifie la version la plus récente d'[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] acceptée.  La version est déterminée selon l'attribut `DataServiceVersion` de l'élément DataService dans les métadonnées du service des données retournées.  Pour plus d'informations, consultez [Contrôle de version d'un service de données](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md).  Lorsque vous spécifiez le paramètre `/dataservicecollection`, vous devez également spécifier `/version:2.0` pour permettre la liaison de données.|  
  
## Voir aussi  
 [Génération de la bibliothèque cliente du service de données](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)   
 [Procédure : ajouter une référence de service de données](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)