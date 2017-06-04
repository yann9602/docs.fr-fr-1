---
title: "&lt;endpointDiscovery&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# &lt;endpointDiscovery&gt;
Spécifie les différents paramètres de découverte d'un point de terminaison, tels que la fonctionnalité de découverte, les portées et toutes les extensions personnalisées de ses métadonnées.  
  
## Syntaxe  
  
```  
  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="String">  
      <endpointDiscovery enabled="Boolean">  
        <scopes>  
          <add scope="URI"/>  
        </scopes>  
        <extensions>  
        </extensions>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|enabled|Valeur booléenne qui spécifie si la fonctionnalité de découverte est activée sur ce point de terminaison.  La valeur par défaut est `false`.|  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<scopes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|Collection d'URI de portée pour le point de terminaison.  Plusieurs URI de portée peuvent être associés au même point de terminaison.|  
|[\<extensions\>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) \[de \<endpointDiscovery\>\]|Collection d'éléments XML qui vous permet de spécifier des métadonnées personnalisées à publier pour un point de terminaison.|  
|\<types\>|Collection d'interfaces à rechercher.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
|||  
  
## Notes  
 Lorsqu'il est ajouté à la configuration de comportement du point de terminaison et si le jeu d'attributs `enabled` a la valeur `true`, cet élément de configuration devient détectable.  De plus, vous pouvez utiliser l'élément enfant [\<scopes\>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md) pour spécifier des URI de portée personnalisés permettant de filtrer des points de terminaison de service pendant la requête, ainsi que l'élément enfant [\<extensions\>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions.md) pour spécifier des métadonnées personnalisées qui doivent être publiées avec les métadonnées détectables standard \(EPR, ContractTypeName, BindingName, Scope et ListenURI\).  
  
 Cet élément de configuration dépend de l'élément [\<serviceDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) qui fournit le contrôle de la fonctionnalité de découverte au niveau du service.  Cela signifie que les paramètres de cet élément sont ignorés si [\<serviceDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) n'est pas présent dans la configuration.  
  
## Exemple  
 L'exemple de configuration suivant spécifie des portées de filtrage et des métadonnées d'extension à publier pour un point de terminaison.  
  
```  
  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
     <endpoint binding="basicHttpBinding"  
              address="calculator"  
              contract="ICalculatorService"  
              behaviorConfiguration="calculatorEndpointBehavior" />  
  </service>  
</services>  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery />  
    </behavior>  
  </serviceBehaviors>  
  <endpointBehaviors>  
    <behavior name="calculatorEndpointBehavior">  
      <endpointDiscovery enabled="true">  
        <scopes>  
          <add scope="http://contoso/test1"/>  
          <add scope="http://contoso/test2"/>  
        </scopes>  
        <extensions>  
          <e:Publisher xmlns:e="http://example.org">  
            <e:Name>The Example Organization</e:Name>  
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>  
            <e:Contact>support@example.org</e:Contact>  
          </e:Publisher>  
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>  
        </extensions>  
      </endpointDiscovery>  
    </behavior>  
  </endpointBehaviors>  
</behaviors>  
  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>