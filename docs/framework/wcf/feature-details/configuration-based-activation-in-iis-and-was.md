---
title: "Activation basée sur la configuration dans les services IIS et WAS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 116d7ec11f141e813aa960b28289031e0cfa8999
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Activation basée sur la configuration dans les services IIS et WAS
Généralement, lorsque vous hébergez un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dans les services IIS (Internet Information Services) ou WAS (Windows Process Activation Service), vous devez fournir un fichier .svc. Le fichier .svc contient le nom du service et une fabrique hôte de service personnalisée facultative. Ce fichier supplémentaire facilite encore la gestion. Grâce à la fonctionnalité d'activation basée sur la configuration, le fichier .svc et, par conséquent, les surcharges associées ne sont plus indispensables.  
  
## <a name="configuration-based-activation"></a>Activation basée sur la configuration  
 L'activation basée sur la configuration prend les métadonnées qui étaient placées dans le fichier .svc et les met dans le fichier Web.config. Dans le <`serviceHostingEnvironment`> élément est un <`serviceActivations`> élément. Dans le <`serviceActivations`> élément sont un ou plusieurs <`add`> éléments, un pour chaque service hébergé. Le <`add`> élément contient des attributs qui vous permettent de définir l’adresse relative pour le service et le type de service ou une fabrique d’hôte de service. L'exemple de code de configuration suivant montre comment cette section est utilisée.  
  
> [!NOTE]
>  Chaque <`add`> élément doit spécifier un service ou un attribut factory. Il est possible de spécifier les deux.  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 Grâce à ce code dans le fichier Web.config, vous pouvez placer le code source du service dans le répertoire App_Code de l'application ou un assembly compilé dans le répertoire Bin de l'application.  
  
> [!NOTE]
>  -   Lors d'une activation basée sur la configuration, le code inline dans les fichiers .svc n'est pas pris en charge.  
> -   Le `relativeAddress` attribut doit être défini comme une adresse relative «\<sous-répertoire > / service.svc » ou « ~ /\<sub/service.svc ».  
> -   Une exception de configuration est levée si vous inscrivez une adresse relative sans extension connue, associée à WCF.  
> -   L'adresse relative spécifiée est relative à la racine de l'application virtuelle.  
> -   En raison du modèle hiérarchique de configuration, les adresses relatives enregistrées au niveau de l'ordinateur et du site sont héritées par les applications virtuelles.  
> -   Les inscriptions dans un fichier de configuration sont prioritaires sur les paramètres d'un fichier .svc, .xamlx, .xoml ou autre.  
> -   Toute '\' (barre oblique inverse) qui se trouve dans un URI envoyé aux services IIS/WAS est automatiquement convertie en '/' (barre oblique). Si une adresse relative contenant un signe '\' est ajoutée et que vous envoyez à IIS un URI utilisant cette adresse relative, la barre oblique inverse est convertie en barre oblique et IIS ne peut pas le faire correspondre à l'adresse relative. IIS envoie des informations de suivi qui indiquent qu'aucune correspondance n'a été trouvée.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [Hébergement de services](../../../../docs/framework/wcf/hosting-services.md)  
 [Vue d’ensemble des Services de Workflow hébergement](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [\<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [Fonctionnalités d’hébergement de Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
