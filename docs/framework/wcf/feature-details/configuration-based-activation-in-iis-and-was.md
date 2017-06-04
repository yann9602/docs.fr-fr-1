---
title: "Activation bas&#233;e sur la configuration dans les services IIS et WAS | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# Activation bas&#233;e sur la configuration dans les services IIS et WAS
Généralement, lorsque vous hébergez un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dans les services IIS \(Internet Information Services\) ou WAS \(Windows Process Activation Service\), vous devez fournir un fichier .svc.Le fichier .svc contient le nom du service et une fabrique hôte de service personnalisée facultative.Ce fichier supplémentaire facilite encore la gestion.Grâce à la fonctionnalité d'activation basée sur la configuration, le fichier .svc et, par conséquent, les surcharges associées ne sont plus indispensables.  
  
## Activation basée sur la configuration  
 L'activation basée sur la configuration prend les métadonnées qui étaient placées dans le fichier .svc et les met dans le fichier Web.config.Dans l'élément \<`serviceHostingEnvironment`\>, se trouve un élément \<`serviceActivations`\>.Dans l'élément \<`serviceActivations`\> se trouvent un ou plusieurs éléments \<`add`\>, un pour chaque service hébergé.L'élément \<`add`\> contient des attributs qui vous permettent de définir l'adresse relative et le type du service ou une fabrique hôte de service.L'exemple de code de configuration suivant montre comment cette section est utilisée.  
  
> [!NOTE]
>  Chaque élément \<`add`\> doit spécifier un attribut de service ou un attribut de fabrique.Il est possible de spécifier les deux.  
  
```  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory=”MyServiceHostFactory”/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 Grâce à ce code dans le fichier Web.config, vous pouvez placer le code source du service dans le répertoire App\_Code de l'application ou un assembly compilé dans le répertoire Bin de l'application.  
  
> [!NOTE]
>  -   Lors d'une activation basée sur la configuration, le code inline dans les fichiers .svc n'est pas pris en charge.  
> -   L'attribut `relativeAddress` doit être défini à une adresse relative telle que « \/\<sous\-répertoire\>\/service.svc » ou « ~\/\<sous\-répertoire\/service.svc ».  
> -   Une exception de configuration est levée si vous inscrivez une adresse relative sans extension connue, associée à WCF.  
> -   L'adresse relative spécifiée est relative à la racine de l'application virtuelle.  
> -   En raison du modèle hiérarchique de configuration, les adresses relatives enregistrées au niveau de l'ordinateur et du site sont héritées par les applications virtuelles.  
> -   Les inscriptions dans un fichier de configuration sont prioritaires sur les paramètres d'un fichier .svc, .xamlx, .xoml ou autre.  
> -   Toute '\\' \(barre oblique inverse\) qui se trouve dans un URI envoyé aux services IIS\/WAS est automatiquement convertie en '\/' \(barre oblique\).Si une adresse relative contenant un signe '\\' est ajoutée et que vous envoyez à IIS un URI utilisant cette adresse relative, la barre oblique inverse est convertie en barre oblique et IIS ne peut pas le faire correspondre à l'adresse relative.IIS envoie des informations de suivi qui indiquent qu'aucune correspondance n'a été trouvée.  
  
## Voir aussi  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>   
 [Hébergement de services](../../../../docs/framework/wcf/hosting-services.md)   
 [Vue d'ensemble de l'hébergement de services de workflow](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)   
 [\<serviceHostingEnvironment\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)   
 [Fonctionnalités d'hébergement de Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=201276)