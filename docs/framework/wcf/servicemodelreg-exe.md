---
title: "Outil d&#39;inscription ServiceModel (ServiceModelReg.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
caps.latest.revision: 26
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 26
---
# Outil d&#39;inscription ServiceModel (ServiceModelReg.exe)
Cet outil de ligne de commande permet de gérer l'inscription des composants WCF et WF sur un ordinateur unique.Dans des circonstances normales vous n'avez pas à utiliser cet outil, car les composants WCF et WF sont configurés lors de l'installation.Mais si vous rencontrez des problèmes avec l'activation de service, vous pouvez essayer d'inscrire les composants à l'aide de cet outil.  
  
## Syntaxe  
  
```  
  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## Notes  
 Cet outil se trouve à l'emplacement suivant :  
  
 %SystemRoot%\\Microsoft.Net\\Framework\\v3.0\\Windows Communication Foundation\\  
  
> [!NOTE]
>  Lorsque l'outil d'inscription ServiceModel est exécuté sur [!INCLUDE[wv](../../../includes/wv-md.md)], la boîte de dialogue **Fonctionnalités de Windows** peut ne pas refléter le fait que l'option **Activation HTTP de Windows Communication Foundation** sous **Microsoft .NET Framework 3.0** est activée.La boîte de dialogue **Fonctionnalités de Windows** est accessible en cliquant sur **Démarrer**, puis sur **Exécuter** et en tapant **OptionalFeatures**.  
  
 Les tableaux suivants décrivent les options qui peuvent être utilisées avec ServiceModelReg.exe.  
  
|Option|Description|  
|------------|-----------------|  
|`-ia`|Installe les composants WCF et WF.|  
|`-ua`|Désinstalle les composants WCF et WF.|  
|`-r`|Répare les composants WCF et WF.|  
|`-i`|Installe les composants WCF et WF spécifiés avec –c.|  
|`-u`|Désinstalle les composants WCF et WF spécifiés avec –c.|  
|`-c`|Installe ou désinstalle un composant :<br /><br /> -   httpnamespace – réservation d'espace de noms HTTP<br />-   tcpportsharing – service de partage de port TCP<br />-   tcpactivation – service d'activation TCP \(non pris en charge sur .NET 4 Client Profile\)<br />-   namedpipeactivation – service d'activation de canal nommé \(non pris en charge sur .NET 4 Client Profile<br />-   msmqactivation – service d'activation MSMQ \(non pris en charge sur .NET 4 Client Profile<br />-   etw – manifestes de suivi d'événements ETW \(Windows Vista ou version ultérieure\)|  
|`-q`|Mode silencieux \(enregistrement des erreurs d'affichage uniquement\)|  
|`-v`|Mode documenté.|  
|`-nologo`|Supprime le message de copyright et de bannière.|  
|`-?`|Affiche le texte de l'aide.|  
  
## Résolution de l'erreur FileLoadException  
 Si vous avez installé des versions antérieures de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sur votre ordinateur, vous pouvez recevoir un message d'erreur `FileLoadFoundException` lorsque vous exécutez l'outil ServiceModelReg pour enregistrer une nouvelle installation.Cela peut se produire même si vous avez supprimé manuellement les fichiers de la précédente installation, mais que vous avez conservé les paramètres machine.config.  
  
 Le message d'erreur est semblable au message suivant.  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Ce message d'erreur indique que l'assembly de la version 2.0.0.0 de System.ServiceModel a été installé par une version antérieure de CTP \(Customer Technology Preview\).La version actuelle de l'assembly System.ServiceModel est la version 3.0.0.0.Par conséquent, vous rencontrerez ce problème lorsque vous souhaiterez installer [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] \(version officielle\) sur un ordinateur sur lequel une version CTP antérieure de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] a été installée, mais n'a pas été complètement désinstallée.  
  
 ServiceModelReg.exe ne peut pas nettoyer les entrées de versions antérieures ; il ne peut pas non plus enregistrer les entrées de la nouvelle version.La seule solution consiste à modifier manuellement le fichier machine.config.Vous trouverez ce fichier à l'emplacement suivant :  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 Si vous exécutez [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sur un ordinateur 64 bits, vous devez également modifier le même fichier à cet emplacement.  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 Recherchez dans ce fichier tous les nœuds XML qui font référence à System.ServiceModel, Version\=2.0.0.0, puis supprimez\-les, ainsi que tous les nœuds enfants.Enregistrez le fichier et réexécutez ServiceModelReg.exe afin de résoudre ce problème.  
  
## Exemples  
 Les exemples suivants indiquent comment utiliser les options les plus courantes de l'outil ServiceModelReg.exe.  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```