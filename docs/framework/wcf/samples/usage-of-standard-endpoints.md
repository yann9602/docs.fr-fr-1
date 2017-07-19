---
title: "Utilisation de points de terminaison standard | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Utilisation de points de terminaison standard
Cet exemple montre comment utiliser des points de terminaison standard dans des fichiers de configuration de service.  Un point de terminaison standard permet à l'utilisateur de simplifier des définitions de point de terminaison en utilisant une propriété unique pour décrire une combinaison adresse, liaison et contrat avec les propriétés supplémentaires qui lui sont associées.  Cet exemple montre comment définir et implémenter un point de terminaison standard personnalisé et comment définir des propriétés spécifiques dans le point de terminaison.  
  
## Détails de l'exemple  
 Les points de terminaison de service peuvent être spécifiés en fournissant trois paramètres : adresse, liaison et contrat.  D'autres paramètres peuvent être fournis : configuration du comportement, en\-têtes, URI d'écoute, et ainsi de suite.  Il peut arriver que certains ou l'ensemble des adresses, liaisons et contrats aient des valeurs qui ne peuvent pas changer.  C'est pourquoi il est possible d'utiliser des points de terminaison standard.  Les points de terminaison d'échange de métadonnées et de découverte en sont des exemples.  Les points de terminaison standard facilitent également l'utilisation en autorisant la configuration de points de terminaison de service sans avoir à fournir des informations d'une nature fixe ou à créer leurs propres points de terminaison standard, afin, par exemple, de faciliter l'utilisation en fournissant un jeu raisonnable de valeurs par défaut, ce qui réduit les commentaires des fichiers de configuration.  
  
 Cet exemple se compose de deux projets : le service qui définit deux points de terminaison standard et le client qui communique avec ce service.  La façon dont les points de terminaison standard du service sont définis dans le fichier de configuration est illustrée dans l'exemple suivant.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <endpointExtensions>  
        <add name="customEndpoint" type="Microsoft.Samples.StandardEndpoints.CustomEndpointCollectionElement, service" />  
      </endpointExtensions>  
    </extensions>  
    <services>  
      <service name="Microsoft.Samples.StandardEndpoints.CalculatorService">  
        <endpoint address="http://localhost:8000/Samples/Service.svc/customEndpoint" contract="Microsoft.Samples.StandardEndpoints.ICalculator" kind="customEndpoint" />  
        <endpoint kind="mexEndpoint" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <standardEndpoints>  
      <customEndpoint>  
        <standardEndpoint property="True" />  
      </customEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
</configuration>  
  
```  
  
 Le premier point de terminaison défini pour le service est du genre `customEndpoint` \(dont la définition est visible dans la section `<standardEndpoints>`\) où la valeur `true` est affectée à la propriété `property`.  C'est le cas d'un point de terminaison personnalisé avec une nouvelle propriété.  Le deuxième point de terminaison correspond à un point de terminaison de métadonnées, où les valeurs d'adresse, de liaison et de contrat sont fixes.  
  
 Pour définir l'élément du point de terminaison standard, une classe qui dérive de `StandardEndpointElement` doit être créée.  Dans le cas de cet exemple, la classe `CustomEndpointElement` a été définie comme indiqué dans l'exemple suivant.  
  
```csharp  
public class CustomEndpointElement : StandardEndpointElement  
{  
    public bool Property  
    {  
        get { return (bool)base["property"]; }  
        set { base["property"] = value; }  
    }  
  
    protected override ConfigurationPropertyCollection Properties  
    {  
        get  
        {  
            ConfigurationPropertyCollection properties = base.Properties;  
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));  
            return properties;  
        }  
    }  
  
    protected override Type EndpointType  
    {  
        get { return typeof(CustomEndpoint); }  
    }  
  
    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)  
    {  
        return new CustomEndpoint();  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)  
    {  
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;  
        customEndpoint.Property = this.Property;  
    }  
  
    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)  
    {  
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;  
        customEndpoint.Property = this.Property;  
    }  
  
    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)  
    {  
    }  
  
    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)  
    {  
    }  
}  
  
```  
  
 Dans la fonction `CreateServiceEndpoint`, un objet `CustomEndpoint` est créé.  Sa définition est représentée dans l'exemple suivant.  
  
```  
public class CustomEndpoint : ServiceEndpoint  
    {  
        public CustomEndpoint()  
            : this(string.Empty)  
        {  
        }  
  
        public CustomEndpoint(string address)  
            : this(address, ContractDescription.GetContract(typeof(ICalculator)))  
        {  
        }  
  
        public CustomEndpoint(string address, ContractDescription contract)  
            : base(contract)  
        {  
            this.Binding = new BasicHttpBinding();  
            this.IsSystemEndpoint = false;  
        }  
  
        public bool Property  
        {  
            get;  
            set;  
        }  
    }  
  
```  
  
 Pour permettre la communication entre service et client, une référence au service est créée dans le client.  Lorsque l'exemple est généré et exécuté, le service s'exécute et le client communique avec lui.  Notez que la référence de service doit être mise à jour à chaque modification du service.  
  
#### Pour utiliser cet exemple  
  
1.  À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez le fichier StandardEndpoints.sln.  
  
2.  Permettez à plusieurs projets de démarrer.  
  
    1.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur la solution Standard Endpoints et sélectionnez **Propriétés**.  
  
    2.  Dans **Propriétés communes**, sélectionnez **Projet de démarrage**, puis cliquez sur **Plusieurs projets de démarrage**.  
  
    3.  Déplacez le projet Service vers le début de la liste, avec l'**Action** **Démarrer**.  
  
    4.  Déplacez le projet Client après le projet Service, également avec l'**Action** **Démarrer**.  
  
         De cette façon, le projet Client est exécuté après le projet Service.  
  
3.  Pour exécuter la solution, appuyez sur F5.  
  
> [!NOTE]
>  Si ces étapes ne fonctionnent pas, vérifiez que votre environnement a été correctement configuré, en procédant comme suit.  
>   
>  1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
> 2.  Pour générer la solution, suivez les instructions indiquées dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
> 3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans la rubrique [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, accédez à la page des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`  
  
## Voir aussi