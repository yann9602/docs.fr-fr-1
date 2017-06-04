---
title: "Metadata Publishing Behavior | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Metadata Publishing Behaviors (exemple) (Windows Communication Foundation)"
  - "comportements de service, exemple de publication de métadonnées"
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
caps.latest.revision: 23
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 23
---
# Metadata Publishing Behavior
Cet exemple montre comment contrôler les fonctionnalités de publication des métadonnées d'un service.Afin d'éviter toute divulgation accidentelle de métadonnées de service potentiellement sensibles, la configuration par défaut des services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] désactive la publication des métadonnées.Ce comportement est sécurisé par défaut, mais il signifie également que vous ne pouvez pas utiliser d'outil d'importation de métadonnées \(tel que Svcutil.exe\) pour générer le code client requis pour appeler le service, à moins que le comportement de publication des métadonnées du service soit activé explicitement dans la configuration.  
  
> [!IMPORTANT]
>  Pour plus de clarté, cet exemple montre comment créer un point de terminaison de publication de métadonnées non sécurisé.De tels points de terminaison sont potentiellement disponibles aux consommateurs non authentifiés anonymes et il est nécessaire de se montrer vigilant et de s'assurer que la divulgation publique des métadonnées d'un service est appropriée avant de déployer de tels points de terminaison.Consultez l'exemple [Point de terminaison de métadonnées sécurisé personnalisée](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) pour obtenir un exemple qui sécurise un point de terminaison de métadonnées.  
  
 Cet exemple est basé sur [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente le contrat de service `ICalculator`.Dans cet exemple, le client est une application console \(.exe\) et le service est hébergé par les services IIS \(Internet Information Services\).  
  
> [!NOTE]
>  La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Pour qu'un service expose des métadonnées, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> doit être configuré sur le service.Lorsque ce comportement est présent, vous pouvez publier des métadonnées en configurant un point de terminaison afin qu'il exposer le contrat <xref:System.ServiceModel.Description.IMetadataExchange> en tant qu'implémentation d'un protocole MEX \(WS\-MetadataExchange\).Par commodité, le nom de configuration abrégé « IMetadataExchange » a été donné à ce contrat.Cet exemple utilise `mexHttpBinding`, qui est une liaison standard équivalente à `wsHttpBinding` dont le mode de sécurité a la valeur `None`.Une adresse relative de « mex » est utilisée dans le point de terminaison. Lorsqu'elle est résolue par rapport à l'adresse de base des services, l'adresse de point de terminaison est http:\/\/localhost\/servicemodelsamples\/service.svc\/mex.La configuration de comportement se présente comme suit :  
  
```  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Le point de terminaison MEX se présente comme suit :  
  
```  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 Cet exemple affecte `true` à la propriété <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> qui expose également les métadonnées du service à l'aide de HTTP GET.Pour activer un point de terminaison de métadonnées HTTP GET, le service doit avoir une adresse de base HTTP.La chaîne de requête `?wsdl` est utilisée sur l'adresse de base du service pour accéder aux métadonnées.Par exemple, pour consulter le WSDL du service dans un navigateur Web, utilisez l'adresse http:\/\/localhost\/servicemodelsamples\/service.svc?wsdl.Vous pouvez également utiliser ce comportement pour exposer des métadonnées sur HTTPS en affectant `true` à <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>.Cela requiert une adresse de base HTTPS.  
  
 Pour accéder au point de terminaison MEX du service, utilisez [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 Cette opération génère un client basé sur les métadonnées du service.  
  
 Pour accéder aux métadonnées du service à l'aide de HTTP GET, pointez votre navigateur sur http:\/\/localhost\/servicemodelsamples\/service.svc?wsdl.  
  
 Si vous supprimez ce comportement et tentez d'ouvrir le service, vous obtenez une exception.Cette erreur se produit car sans le comportement, le point de terminaison configuré avec le contrat `IMetadataExchange` n'a aucune implémentation.  
  
 Si vous affectez `false` à `HttpGetEnabled`, la page d'aide CalculatorService s'affiche à la place des métadonnées du service.  
  
### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée dans la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, rendez\-vous sur la page \(éventuellement en anglais\) des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## Voir aussi