---
title: '&lt;routing&gt; of &lt;serviceBehavior&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4e5c27b2b276e6659680dabfd9460c6d072bad3a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ltroutinggt-of-ltservicebehaviorgt"></a>&lt;routing&gt; of &lt;serviceBehavior&gt;
Fournit un accès au service de routage au moment de l'exécution afin d'autoriser une modification dynamique de la configuration de routage.  
  
 \<système. ServiceModel >  
\<comportements >  
\<serviceBehaviors >  
\<comportement >  
\<routage >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String" 
               routeOnHeadersOnly="Boolean" 
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|filterTable|Chaîne qui spécifie le nom de la table de routage contenant les filtres destinés à être évalués par le service de routage. Cette valeur doit correspondre à la `name` attribut d’un [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) élément dans le [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) section.|  
|routeOnHeaderOnly|Valeur booléenne qui spécifie si le filtre doit examiner à la fois le corps du message et l'en-tête, ou l'en-tête uniquement. La valeur par défaut est `true`.|  
|soapProcessingEnabled|Valeur booléenne qui spécifie si le traitement SOAP doit avoir lieu.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un élément de comportement.|  
  
## <a name="remarks"></a>Remarques  
 Lorsqu'il est ajouté à la configuration de comportement du service, cet élément de configuration active le routage pour le service. Vous pouvez spécifier la table de routage réelle que le service doit utiliser dans cet élément.  
  
 Cette section de configuration vous permet de modifier immédiatement vos paramètres de routage lorsque votre modèle de déploiement change. Au moment de l'exécution, vous pouvez inscrire votre propre extension de routage avec de nouveaux paramètres de routage. Le service de routage commence alors à utiliser les informations de configuration mises à jour pour les nouveaux messages et sessions, en laissant les messages/sessions en cours utiliser les règles qui étaient en place lorsqu'ils ont démarré.  Vous avez ainsi la possibilité de reconfigurer le service de routage au moment de l'exécution, sans interruption de session ni recyclage.  
  
