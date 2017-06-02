---
title: "&lt;generatePublisherEvidence&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<generatePublisherEvidence> (élément)"
  - "generatePublisherEvidence (élément)"
ms.assetid: 7d208f50-e8d5-4a42-bc1a-1cf3590706a8
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# &lt;generatePublisherEvidence&gt;, &#233;l&#233;ment
Spécifie si le runtime crée la preuve <xref:System.Security.Policy.Publisher> pour la sécurité d'accès du code \(CAS\).  
  
## Syntaxe  
  
```  
<generatePublisherEvidence    
   enabled="true|false"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime crée la preuve <xref:System.Security.Policy.Publisher>.|  
  
## Attribut enabled  
  
|Valeur|Description|  
|------------|-----------------|  
|`false`|Ne crée pas de preuve <xref:System.Security.Policy.Publisher>.|  
|`true`|Crée une preuve <xref:System.Security.Policy.Publisher>.  Il s'agit de la valeur par défaut.|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## Notes  
  
> [!NOTE]
>  Dans [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] et version ultérieure, cet élément n'a aucun effet sur les temps de chargement des assemblys.  Pour plus d'informations, consultez la section « Simplification de la stratégie de sécurité » dans [Modifications de sécurité](../../../../../docs/framework/security/security-changes.md).  
  
 Le common language runtime \(CLR\) tente de vérifier la signature Authenticode au moment du chargement pour créer la preuve <xref:System.Security.Policy.Publisher> pour l'assembly.  Toutefois, par défaut, la plupart des applications n'ont pas besoin de preuve <xref:System.Security.Policy.Publisher>.  La stratégie CAS standard ne compte pas sur <xref:System.Security.Policy.PublisherMembershipCondition>.  Vous devez éviter le coût de démarrage inutile associé à la vérification de la signature de l'éditeur à moins que votre application ne s'exécute sur un ordinateur possédant une stratégie CAS personnalisée, ou n'ait l'intention de satisfaire des demandes pour <xref:System.Security.Permissions.PublisherIdentityPermission> dans un environnement de confiance partielle. \(Les demandes pour les autorisations d'identité réussissent toujours dans un environnement de confiance totale.\)  
  
> [!NOTE]
>  Nous recommandons que les services utilisent l'élément `<generatePublisherEvidence>` pour améliorer les performances au démarrage.  L'usage de cet élément peut également permettre d'éviter des délais pouvant provoquer une expiration de délai d'attente et l'annulation du démarrage du service.  
  
## Fichier de configuration  
 Cet élément peut être utilisé uniquement dans le fichier de configuration de l'application.  
  
## Exemple  
 L'exemple suivant indique comment utiliser l'élément `<generatePublisherEvidence>` pour désactiver le contrôle de la stratégie CAS du serveur de publication pour une application.  
  
```  
<configuration>  
    <runtime>  
        <generatePublisherEvidence enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des paramètres d'exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)