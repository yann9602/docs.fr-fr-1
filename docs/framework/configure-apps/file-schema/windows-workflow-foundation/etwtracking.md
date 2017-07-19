---
title: "&lt;etwTracking&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cb45c82e-6ea1-4c4d-924c-118a25ae1f35
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &lt;etwTracking&gt;
Comportement de service qui permet à un service d'utiliser le suivi ETW à l'aide de <xref:System.Activities.Tracking.ETWTrackingParticipant>.  
  
## Syntaxe  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
      <etwTracking profileName=”String” />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|profileName|Chaîne qui spécifie le nom du modèle de suivi a associé à ce comportement.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<behavior\> de \<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|Spécifie un élément de comportement.|  
  
## Notes  
 Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration configure un participant au suivi sur un service de flux de travail.  
  
 Les participants au suivi permettent d'obtenir les données de suivi émises du flux de travail et de les stocker dans différents médias.  De la même manière, tout post\-traitement effectué sur les enregistrements de suivi peut également être réalisé dans le participant au suivi.  
  
## Exemple  
 L'exemple suivant présente la configuration du participant au suivi ETW standard dans le fichier Web.config.  
  
 L'ID de fournisseur dont se sert le participant au suivi ETW pour écrire les enregistrements de suivi dans une session ETW est défini dans la section **\<diagnostics\>**.  Un profil est associé au participant au suivi pour spécifier les enregistrements de suivi auxquels il est abonné.  Ce profil est défini par l'attribut **profileName** de l'élément **\<add\>**.  Une fois ces paramètres définis, le participant au suivi est ajouté au comportement de service **\<etwTracking\>**.  Les participants au suivi sélectionnés sont ajoutés aux extensions de l'instance de flux de travail, afin qu'ils commencent à recevoir les enregistrements de suivi.  
  
```  
  
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## Voir aussi  
 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>   
 <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>   
 [Suivi et traçage de workflow](../../../../../docs/framework/windows-workflow-foundation//workflow-tracking-and-tracing.md)   
 [Participants de suivi](../../../../../docs/framework/windows-workflow-foundation//tracking-participants.md)